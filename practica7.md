# PROLOG (Practica 7)

## Índice

- [Ejercicio 3](#ejercicio-3)  
- [Ejercicio 4](#ejercicio-4)  
- [Ejercicio 5](#ejercicio-5)  
- [Ejercicio 6](#ejercicio-6)  
- [Ejercicio 7](#ejercicio-7)  
- [Ejercicio 8](#ejercicio-8)  
- [Ejercicio 9](#ejercicio-9)  
- [Ejercicio 10](#ejercicio-10)  
- [Ejercicio 11](#ejercicio-11)  
- [Ejercicio 12](#ejercicio-12)  
- [Ejercicio 13](#ejercicio-13)  
- [Ejercicio 15](#ejercicio-15)  
- [Ejercicio 16](#ejercicio-16)  
- [Ejercicio 17](#ejercicio-17)  
- [Ejercicio 18](#ejercicio-18)  
- [Ejercicio 19](#ejercicio-19)  
- [Ejercicio 20](#ejercicio-20)  

## Ejercicio 3

```prolog
  model('renault', 'clio')
```

**Redultado:**

```prolog
  false
```

## Ejercicio 4

```prolog
  model(X, 'renault')
```

**Redultado:**

```prolog
  X = clio
```

## Ejercicio 5

```prolog
  country(X, X)
```

**Redultado:**

```prolog
  false
```

## Ejercicio 6

**A):**

```prolog
  model(X, Brand), country(Brand, 'alemania')
```

**Redultado:**

```prolog
  X = golf,
  Brand = volkswagen;
  X = touran,
  Brand = volkswagen;
  X = corsa,
  Brand = opel
```

**B):**

```prolog
  isRelated('cordoba', X)
```
**Redultado:**

```prolog
  X = ibiza ;
  X = altea ;
  X = twingo ;
  X = ibiza ;
  X = clio ;
  X = '2008' ;
  X = corsa ;
  X = ibiza ;
  X = cordoba ;
  X = golf ;
  X = clio ;
  X = twingo ;
  X = corsa ;
```

## Ejercicio 7

```prolog
  isCountryOf(A,B) :- isModelFrom(B,A). 
  isClassic(A) :- since(A,B), B < 1995.
```

**A):**

```prolog
  isCountryOf(Country,'megane').
```  

**Redultado:**

```prolog
  Country = francia.
```

**B):**

```prolog
  isClassic(X)
```  

**Redultado:**

```prolog
  X = ibiza ;
  X = cordoba ;
  X = golf ;
  X = clio ;
  X = twingo ;
  X = corsa ;
```

## Ejercicio 8

```prolog
  isRelated(A,B) :- isSameBrand(A,B).
  isRelated(A,B) :- isSameYear(A,B).
  isRelated(A,B) :- segment(A,C), segment(B,C), A \== B.
  isRelated(A,B) :- isClassic(A), isClassic(B).
```

**Redultado:**

```prolog
  isRelated(golf, X).
  X = touran ;
  X = altea ;
  X = megane ;
  X = 'scAnic' ;
  X = '3008' ;
  X = ibiza ;
  X = cordoba ;
  X = golf ;
  X = clio ;
  X = twingo ;
  X = corsa ;  
```

## Ejercicio 9

```prolog
  date(10, nov, 2030) = date(X, nov,2030).
```

**Redultado:**

```prolog
  X = 10 ;
```

## Ejercicio 10

```prolog
  model(X, volkswagen) = model(golf, Y).  
```

**Redultado:**

```prolog
  X = golf ;
  X = volkswagen ;
```

## Ejercicio 11

```prolog
  flight(valencia, london, DepartureDay, DepartureTime, ArrivalDay, ArrivalTime, Duration, Price). 
```

**Redultado:**

```prolog
  DepartureDay = ArrivalDay, ArrivalDay = date(10, nov, 2030),
  DepartureTime = time(16, 5),
  ArrivalTime = time(17, 35),
  Duration = 90,
  Price = 50.
```

## Ejercicio 12

```prolog
  flight(madrid, Destination, date(10, nov, 2030), _, _, _, _, _).
flight(Origin, Destination, _, time(13, 05), _, _, _, _).
flight(Origin, Destination, _, time(H, M), _, _, _, _), H >= 16.
```

## Ejercicio 13

```prolog
  connection_same_day(Origin, Destination, date(10, nov, 2030)).
```

## Ejercicio 15

```prolog
  isRelated(touran, X).
```

## Ejercicio 16

```prolog
  connection_same_day(Origin, Destination, Connection).
```

**Redultado:**

```prolog
  Origin = barcelona,
  Destination = london,
  Connection = date(10, nov, 2030)
```

## Ejercicio 17

```prolog
  connection_same_day(Origin, Destination, Connection).
```

**Redultado:**

```prolog
  1 = 2.        % Falso
  X = 2.        % X toma el valor de 2
  Y = X.        % Y toma el valor de X, pero debe ser instanciado
  X = 8, X = Y. % X se toma el valor de 8, luego Y también toma el valor 8
  X = Y, X = 8. % Primero X y Y son iguales, luego ambos toman el valor 8

```

## Ejercicio 18

```prolog
  1 + 2 = 3.
```

**Redultado:**

```prolog
  % Se obtiene el siguiente error:
  ERROR: Arguments are not sufficiently instantiated

```

## Ejercicio 19

**A):**

```prolog
  factorial(6,Y).
```

**Redultado:**

```prolog
  % Y = 720
```

**B):**

```prolog
  factorial(X, 24). 
```

**Redultado:**

```prolog
  % Deberia encuentrar valores de X con factorial(X) = 24 (no funciona de forma inversa)
```

## Ejercicio 20

La opcion 2