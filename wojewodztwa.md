% Kolory dostępne do kolorowania mapy
color(red).
color(green).
color(blue).
color(yellow).

% Relacje sąsiedztwa (graf nieskierowany)
neighbor(dolnoslaskie, opolskie).
neighbor(opolskie, slaskie).
neighbor(slaskie, malopolskie).
neighbor(malopolskie, swietokrzyskie).
neighbor(swietokrzyskie, lodzkie).
neighbor(lodzkie, opolskie).
neighbor(lodzkie, slaskie).
neighbor(lodzkie, dolnoslaskie).

% Sąsiedztwo jest symetryczne
connected(X, Y) :- neighbor(X, Y).
connected(X, Y) :- neighbor(Y, X).

% Zbieranie unikalnych województw z faktów neighbor/2
all_regions(Regions) :-
    findall(X, (neighbor(X, _); neighbor(_, X)), All),
    sort(All, Regions).  % sort usuwa duplikaty i sortuje alfabetycznie

% Główna funkcja kolorowania mapy
color_map([], []).
color_map([Region|Rest], [(Region, Color)|ColoredRest]) :-
    color(Color),
    color_map(Rest, ColoredRest),
    \+ (member((OtherRegion, Color), ColoredRest),
        connected(Region, OtherRegion)).

% Startowe zapytanie
color_poland(ColoredMap) :-
    all_regions(Regions),
    color_map(Regions, ColoredMap).


?- color_poland(Map).
