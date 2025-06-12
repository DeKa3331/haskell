
addMe :: Integer -> Integer -> Integer
addMe x y = x + y  -- poprawka: operator + musi być między argumentami

main :: IO ()
main = do
  putStr "Sum of x + y = "
  print (10 `addMe` 25)  -- infix


zad2

square :: Num a => a -> a
square x = x * x

cube :: Num a => a -> a
cube x = x * x * x

average :: Fractional a => a -> a -> a
average x y = (x + y) / 2



zad3


-- Wersja I – if..else
solveQuadraticIf :: Double -> Double -> Double -> String
solveQuadraticIf a b c =
  let d = b*b - 4*a*c
  in if d > 0 then
       let x1 = (-b + sqrt d) / (2*a)
           x2 = (-b - sqrt d) / (2*a)
       in "Dwa pierwiastki: " ++ show x1 ++ ", " ++ show x2
     else if d == 0 then
       let x = -b / (2*a)
       in "Jeden pierwiastek: " ++ show x
     else
       "Brak pierwiastków rzeczywistych"

-- Wersja II – strażnicy (guards)
solveQuadratic :: Double -> Double -> Double -> String
solveQuadratic a b c
  | d > 0 = "Dwa pierwiastki: " ++ show x1 ++ ", " ++ show x2
  | d == 0 = "Jeden pierwiastek: " ++ show x
  | otherwise = "Brak pierwiastków rzeczywistych"
  where
    d = b*b - 4*a*c
    x1 = (-b + sqrt d) / (2*a)
    x2 = (-b - sqrt d) / (2*a)
    x  = -b / (2*a)



zad4
factorial :: Integer -> Integer
factorial 0 = 1
factorial n = n * factorial (n - 1)


zad5

fibonacci :: Int -> Integer
fibonacci 0 = 0
fibonacci 1 = 1
fibonacci n = fibonacci (n - 1) + fibonacci (n - 2)


zad6

minmax :: (Ord a, Num a) => a -> a -> a -> a
minmax x y z = maximum [x, y, z] - minimum [x, y, z]


zad7

sumOfSquares :: Num a => a -> a -> a
sumOfSquares x y = x*x + y*y

zad8

sumOfSquares :: Num a => a -> a -> a
sumOfSquares x y = x*x + y*y

//teraz polaczone:



-- Main.hs

addMe :: Integer -> Integer -> Integer
addMe x y = x + y

square :: Num a => a -> a
square x = x * x

cube :: Num a => a -> a
cube x = x * x * x

average :: Fractional a => a -> a -> a
average x y = (x + y) / 2

solveQuadraticIf :: Double -> Double -> Double -> String
solveQuadraticIf a b c =
  let d = b*b - 4*a*c
  in if d > 0 then
       let x1 = (-b + sqrt d) / (2*a)
           x2 = (-b - sqrt d) / (2*a)
       in "Dwa pierwiastki: " ++ show x1 ++ ", " ++ show x2
     else if d == 0 then
       let x = -b / (2*a)
       in "Jeden pierwiastek: " ++ show x
     else
       "Brak pierwiastków rzeczywistych"

solveQuadratic :: Double -> Double -> Double -> String
solveQuadratic a b c
  | d > 0     = "Dwa pierwiastki: " ++ show x1 ++ ", " ++ show x2
  | d == 0    = "Jeden pierwiastek: " ++ show x
  | otherwise = "Brak pierwiastków rzeczywistych"
  where
    d  = b*b - 4*a*c
    x1 = (-b + sqrt d) / (2*a)
    x2 = (-b - sqrt d) / (2*a)
    x  = -b / (2*a)

factorial :: Integer -> Integer
factorial 0 = 1
factorial n = n * factorial (n - 1)

fibonacci :: Int -> Integer
fibonacci 0 = 0
fibonacci 1 = 1
fibonacci n = fibonacci (n - 1) + fibonacci (n - 2)

minmax :: (Ord a, Num a) => a -> a -> a -> a
minmax x y z = maximum [x, y, z] - minimum [x, y, z]

sumOfSquares :: Num a => a -> a -> a
sumOfSquares x y = x*x + y*y

lastDigit :: Integer -> Integer
lastDigit n = abs n `mod` 10

main :: IO ()
main = do
  putStrLn "Zadanie 1: addMe w trybie infix"
  print (10 `addMe` 25)

  putStrLn "\nZadanie 2:"
  print (square 4)
  print (cube 3)
  print (average 10 5)

  putStrLn "\nZadanie 3: równanie kwadratowe (if)"
  putStrLn (solveQuadraticIf 1 (-3) 2)

  putStrLn "Zadanie 3: równanie kwadratowe (guards)"
  putStrLn (solveQuadratic 1 2 1)

  putStrLn "\nZadanie 4: silnia z 5"
  print (factorial 5)

  putStrLn "\nZadanie 5: 10. wyraz Fibonacciego"
  print (fibonacci 10)

  putStrLn "\nZadanie 6: różnica min/max"
  print (minmax 7 1 4)

  putStrLn "\nZadanie 7: suma kwadratów"
  print (sumOfSquares 3 4)

  putStrLn "\nZadanie 8: ostatnia cyfra"
  print (lastDigit 42)
  print (lastDigit (-17))

