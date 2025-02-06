# PROLOG (Practica 8)

## Índice

- [Ejercicio 1](#ejercicio-1)  
- [Ejercicio 2](#ejercicio-2)  
  - [E2 Consulta 1](#e2-consulta-1)  
  - [E2 Consulta 2](#e2-consulta-2)  
  - [E2 Consulta 3](#e2-consulta-3)  
  - [E2 Consulta 4](#e2-consulta-4)  
  - [E2 Consulta 5](#e2-consulta-5)  
  - [Efecto del subrayado](#efecto-del-subrayado-_)  
- [Ejercicio 3](#ejercicio-3)  
  - [E3 Consulta 1](#e3-consulta-1)  
  - [E3 Consulta 2](#e3-consulta-2)  
- [Ejercicio 4](#ejercicio-4)  
- [Ejercicio 5](#ejercicio-5)  
- [Ejercicio 6](#ejercicio-6)  
- [Ejercicio 7](#ejercicio-7)  
- [Ejercicio 8](#ejercicio-8)  
- [Ejercicio 9](#ejercicio-9)  
- [Ejercicio 10](#ejercicio-10)  
- [Ejercicio 11](#ejercicio-11)  


## Ejercicio 1

Edita un programa Prolog e introduce los siguientes hechos

```prolog
  countTo(1,[1]).
  countTo(2,[1,2]).
  countTo(3,[1,2,3]).
  countTo(4,[1,2,3,4]).
```

Carga el codigo y escribe las consultas:

```prolog
  countTo(X,[_,_,_,Y]).
  countTo(X,[_,_,_|Y]).
```

**¿Es Y un elemento o una lista en cada caso?**

- En la **primera** consulta, Y es un elemento si la lista tiene al menos 4 elementos, o la consulta falla si no hay suficientes elementos.

- En la **segunda** consulta, Y es una lista (puede ser vacía) si hay al menos tres elementos, de lo contrario, la consulta falla.


## Ejercicio 2

Prueba las siguientes consultas, ¿Que ves? ¿Por que?  ¿Que efecto tiene usar el simbolo de subrayado?

```prolog
  countTo(4,[H|T]).
  countTo(4,[H1,H2|T]).
  countTo(4,[_,X|_]).
  countTo(2,[H1,H2|T]).
  countTo(2,[H1,H2,H3|T]).
```

### E2 Consulta 1

```prolog
  countTo(4,[H|T]).
```

- Análisis:

  [H|T] es un patrón que descompone una lista en:
  H: El primer elemento de la lista.
  T: El resto de la lista después del primer elemento.

- Resultado:
  
  Con el hecho countTo(4, [1, 2, 3, 4]):

  H se unifica con el primer elemento: H = 1.
  T se unifica con el resto de la lista: T = [2, 3, 4].
  Para otros hechos (por ejemplo, countTo(3, [1, 2, 3])), esta consulta fallará porque solo se evalúan los hechos donde X = 4.

- ¿Qué ves?

  Prolog divide correctamente la lista en el primer elemento (H) y el resto (T).

### E2 Consulta 2

```prolog
  countTo(4,[H1,H2|T]).
```

- Análisis:

  [H1, H2|T] descompone la lista en:
  H1: El primer elemento.
  H2: El segundo elemento.
  T: El resto de la lista después de los dos primeros elementos.

- Resultado:

  Con el hecho countTo(4, [1, 2, 3, 4]):

  H1 = 1.
  H2 = 2.
  T = [3, 4].

- ¿Qué ves?

  Prolog descompone correctamente la lista en sus dos primeros elementos (H1 y H2) y el resto (T).


### E2 Consulta 3

```prolog
  countTo(4,[_,X|_]).
```

- Análisis:
  
  [_, X|_] ignora:
  El primer elemento (_).
  X se unifica con el segundo elemento de la lista.
  El resto de la lista también se ignora (_|_).

- Resultado:
  
  Con el hecho countTo(4, [1, 2, 3, 4]):

  El primer elemento (1) se ignora.
  X = 2, que es el segundo elemento.

- ¿Qué ves?

  Prolog extrae únicamente el segundo elemento (X) y descarta todo lo demás.

### E2 Consulta 4:

```prolog
  countTo(2, [H1, H2|T]).
```

- Análisis:
  
  [H1, H2|T] descompone la lista en:
  
  - H1: El primer elemento.

  - H2: El segundo elemento.

  - T: El resto de la lista después de los dos primeros elementos.

- Resultado:
  
  Con el hecho countTo(2, [1, 2])

  - H1 = 1.

  - H2 = 2.

  - T = [] (la lista no tiene más elementos).

- ¿Qué ves?

  Prolog descompone la lista correctamente, incluso cuando T es la lista vacía ([]).

### E2 Consulta 5

```prolog
 - countTo(2, [H1, H2, H3|T]).
```

- Análisis:
  
  [H1, H2, H3|T] busca descomponer una lista con al menos 3 elementos:
  
  - H1: El primer elemento.
  
  - H2: El segundo elemento.
  
  - H3: El tercer elemento.
  
  - T: El resto de la lista después de los tres primeros elementos.

- Resultado:

Con el hecho countTo(2, [1, 2]), esta consulta falla porque no hay suficientes elementos en la lista para unificar H3.

- ¿Qué ves?

Prolog requiere que la lista tenga al menos 3 elementos para que esta consulta funcione. Si no es así, falla.

### Efecto del subrayado (_)

- **Ignorar valores**: El subrayado (_) le indica a Prolog que no importa el valor de esa posición en la lista. Esto permite simplificar las consultas si no necesitas usar ciertos elementos. 

- **No unifica ni reutiliza**: A diferencia de variables normales, _ no se unifica ni reutiliza su valor. Por ejemplo:

  En [_, _, _|_], cada _ ignora una posición distinta de la lista.
  No hay dependencia entre los valores ignorados.

- **Flexibilidad**: Es útil cuando solo te interesa una parte específica de la lista y quieres ignorar el resto.

## Ejercicio 3

Prueba las siguientes consultas, escribiendo *“;”* tras cada respuesta del interprete para explorar todo el espacio de soluciones:

```prolog
  member(2,[5,2,3,2]).
  member(X,[5,2,3]).
```

### E3 Consulta 1

```prolog
  member(2, [5,2,3,2]).
```

- **Descripción:** El predicado member/2 verifica si el elemento 2 es un miembro de la lista [5, 2, 3, 2]. Prolog busca coincidencias una por una, explorando todas las apariciones de 2.

- **Resultado esperado:** Prolog encuentra la primera ocurrencia de 2 en la lista en la segunda posición. Al escribir **";"**, Prolog continúa buscando y encuentra la segunda ocurrencia de 2 en la lista en la última posición

### E3 Consulta 2

```prolog
  member(X, [5,2,3]).
```

- **Descripción:** En esta consulta, X es una variable libre. El predicado member/2 unifica X con cada elemento de la lista [5, 2, 3] uno por uno.

- **Resultado esperado:** 
  - Prolog unifica X con el primer elemento de la lista dando como reultado **X = 5 ;**

  - Al escribir ;, Prolog unifica X con el segundo elemento de la lista dando como reultado **X = 2 ;**

  - Al escribir ; nuevamente, Prolog unifica X con el tercer elemento de la lista dando como reultado **X = 3 ;**

## Ejercicio 4

Escribe tu propio predicado mymember a partir del siguiente codigo (con errores) que debes corregir para obtener la solucion.

```prolog
  mymember(E,[E,_]).
  mymember(E,[H|L]) :- mymember(H,L).
```

Correccion:

```prolog
  % Caso base: E es el primer elemento de la lista.
  mymember(E, [E|_]). 

  % Caso recursivo: E está en la cola de la lista.
  mymember(E, [_|L]) :- mymember(E, L).
```

## Ejercicio 5

Define un predicado llamado myappend que haga exactamente lo mismo que append pero estando  ́este definido por ti mismo. El codigo siguiente es un punto de comienzo pero hay un error en  ́el que debes encontrar y corregir.

```prolog
  myappend([],L,L).
  myappend([E|L1],L2,[X|L3]) :- X = E, myappend(L1,L2,L1).
```

Codigo corregido.

```prolog
  % Caso base: concatenar una lista vacía con L devuelve L.
  myappend([], L, L).

  % Caso recursivo: añade el primer elemento de la primera lista al resultado de concatenar el resto.
  myappend([E|L1], L2, [E|L3]) :-
  myappend(L1, L2, L3).
```

## Ejercicio 6

Prueba las siguientes consultas, escribiendo ";" tras cada respuesta del int ́erprete para explorar todo el espacio de soluciones:

```prolog
  append([a,Y],[Z,d],[X,b,c,W]).
  append(L1,L2,[a,b,c,d]).
```

## Ejercicio 7

Escribe un predicado binario swap que acepta una lista y genera una lista similar con los dos primeros elementos intercambiados.

```prolog 
  % Caso base: listas con menos de dos elementos no cambian.
  swap([], []).
  swap([X], [X]).

  % Caso principal: intercambiar los dos primeros elementos.
  swap([A, B | Rest], [B, A | Rest]).
```

## Ejercicio 8

¿Que hace el siguiente predicado misterioso y porque?

```prolog
  mistery([],0).
  mistery([_|T],N) :- mistery(T,M), N is M+1.
```

- **Descripción de su funcionamiento**

  - Caso base (mistery([], 0)):

    - Si la lista es vacía ([]), el segundo argumento (N) se unifica con 0.
    
    - Esto indica que la longitud de una lista vacía es 0.

  - Caso recursivo (mistery([_|T], N)):

    Para una lista no vacía, el predicado:

    - Ignora el primer elemento de la lista (representado por _).
    
    - Llama recursivamente a sí mismo con la cola de la lista (T) para calcular su longitud (M).

    - Incrementa el valor resultante (M) en 1 y lo unifica con N.

- **¿Qué hace realmente?**

  El predicado mistery/2 calcula la longitud de una lista.

  - El primer argumento es una lista.
    
  - El segundo argumento es la longitud de esa lista.

## Ejercicio 9 

Completa el siguiente programa Prolog para que implemente la operaci ́on de comprobar si una coleccion de elementos es subconjunto de otra:

```prolog
  subset([],_).
  subset([A|X],Y) :- member(A,Y),    XXXXXXXXX                .  
```

Options:

- A) subset(X,Y)
- B) append(X,[A],Y)
- C) subset(Y,X)
- D) member(X,Y)

El resultado es: **A**

```prolog
  subset([], _).
  subset([A|X], Y) :- member(A, Y), subset(X, Y).
```

## Ejercicio 10 

Completa el siguiente programa Prolog que comprueba si una lista est ́a ordenada:

```prolog
  sorted([]).
  sorted([_]).

  XXXXXXXXXXXXXXXXXX:- X =< Y, sorted([Y|Ys]).

````

Options:

- A) sorted([X|Y,Ys])
- B) sorted([X,[Y|Ys]])
- C) sorted([X,Y|Ys])
- D) sorted(X,Y,Ys)

El resultado es: **C**

```prolog
  sorted([]).                 % Caso base: Una lista vacía está ordenada.
  sorted([_]).                % Caso base: Una lista con un solo elemento está ordenada.
  sorted([X, Y | Ys]) :-      % Caso recursivo: Para una lista con al menos dos elementos,
  X =< Y,                 % el primer elemento debe ser menor o igual al segundo,
  sorted([Y | Ys]).       % y el resto de la lista ([Y | Ys]) también debe estar ordenada.

```

## Ejercicio 11

Completa el siguiente programa l ́ogico para que, dado un entero y una lista de enteros, elimine las ocurrencias de dicho entero de la lista. Los predicados predefinidos “==” y “\==” representan la igualdad y la desigualdad, respectivamente. Por ejemplo, la llamada
remove(3,[1,2,3,1,2,3],L) computa la respuesta L = [1,2,1,2].

```prolog
  remove(_,[],[]).
  remove(C,[X|R],L) :- X == C, remove(C,R,L).
  remove(C,[X|R],W) :- X \== C, , .
```

Options:

- A) remove(C,R,L), W = [X|L]
- B) remove(C,R,W), L = [X|W]
- C) remove(C,R,L), W = L
- D) remove(C,[X|R],L), W = L

La respuesta es: **A**

```prolog
  remove(_, [], []).                     % Caso base: Eliminar de una lista vacía resulta en una lista vacía.
  remove(C, [X|R], L) :- X == C,         % Caso 1: Si el elemento actual es igual al que queremos eliminar,
  remove(C, R, L).                   % simplemente procesamos el resto de la lista sin incluirlo en el resultado.
  remove(C, [X|R], W) :- X \== C,        % Caso 2: Si el elemento actual es distinto,
  remove(C, R, L),                   % procesamos el resto de la lista,
  W = [X|L].                         % y añadimos el elemento actual al resultado.
```