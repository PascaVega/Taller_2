# Taller 2
| Nombre                 | Identificación | Grupo | Trabajo          |
|------------------------|----------------|-------|------------------|
| Angélica Pascagaza Vega| 1031652163     |   5   | Trabajo individual |

## Solución del taller
<table cellspacing="1" bgcolor="" align="center">
  <tr bgcolor="#252582">
    <th><b>Taller 2 - Parte 1</b></th>
  </tr>
  <tr bgcolor="#e4e4ed">
    <td style="color:#141414" align="center">Desarrollar un programa que ingrese un número entero n y separe todos los digitos que componen el número.</td>
  </tr>
  <tr bgcolor="#e4e4ed">
    <td style="color:#141414" align="center">Para separar los digitos, primero se elimina el punto del número flotante al igual que el signo - en caso de que el número sea negativo. Luego se convierte en número en una cadena y se separan los digitos. Para finalizar, se verifica si el último número después del punto es un cero y se elimina (dado que ese cero es agregado por defecto al convertir el número en un flotante). </td>
  </tr>
</table>

**Parte 1**
```python
#TALLER 2 - Parte 1
#Desarrollar un programa que ingrese un número entero n y separe todos los digitos que componen el número.  

def introducir():
    #Se introduce el número como flotante
    num : float = float(input("Ingrese el número: "))
    #Se llama a la función para separar el número
    separar_numero(num)
    return

def separar_numero(num : float):
    #Se convierte al numero en una cadena
    numero : str = str(num)
    #Se separan los digitos
    digitos : list = [digito for digito in numero]
    #Si el número es menor a 0 se remueve el - de la lista
    if num < 0:
        digitos.remove("-")
    #Se remueve el punto de la lista
    digitos.remove(".")
    #Se convierte los elementos de la lista en enteros
    digitos_enteros : list = [int(digito) for digito in digitos]
    #Se elimina el cero que no fue ingresado por el usuario
    if digitos_enteros[-1] == 0:
        digitos_enteros.pop(-1)
    #Se imprime el resultado
    print(f"Los digitos del número son: {digitos_enteros}")
    return

def continuar() -> int:
    #El usuario decide si desea repetir el programa
    opcion : int = int(input("¿Desea continuar? Marque 1 (Sí) o 2 (No): "))
    return opcion

if __name__ == "__main__":
    #Inicia el programa
    print("Programa para separar los digitos de un número.")
    #El programa se repetira tantas veces como el usuario lo desee
    while True:
        introducir()
        opcion : int = continuar()
        if opcion == 2:
            break
        elif opcion != 1 and 2:
            print("SintaxError")
            break

# ! /\|=\/ 
```

<table cellspacing="1" bgcolor="" align="center">
  <tr bgcolor="#252582">
    <th><b>Taller 2 - Parte 2</b></th>
  </tr>
  <tr bgcolor="#e4e4ed">
    <td style="color:#141414" align="center">Desarrollar un programa que ingrese un número flotante n y separe su parte entera de la parte decimal. Luego entregue los dígitos tanto de la parte entera como de la decimal.</td>
  </tr>
  <tr bgcolor="#e4e4ed">
    <td style="color:#141414" align="center">Para este ejercicio, se separan los caracteres de la cadena, luego se define el punto como una referencia y a partir de allí se separan en dos listas los digitos enteros y los decimales.</tr>
</table>

**Parte 2**
```python
#TALLER 2 - Parte 2
#Desarrollar un programa que ingrese un número flotante n y separe su parte entera de la parte decimal.
#Luego entregue los dígitos tanto de la parte entera como de la decimal.

def introducir():
    #Se introduce el número como flotante
    num : float = float(input("Ingrese el número: "))
    #Se llama a la función para separar el número
    separar_numero(num)
    return

def separar_numero(num : float):
    #Se convierte al numero en una cadena
    numero : str = str(num)
    #Se separan los digitos
    digitos : list = [digito for digito in numero]
    #Se obtiene la ubicación del punto
    ubicacion_decimal : int = digitos.index(".")
    #Si el número es menor a 0 se remueve el - de la lista
    if num < 0:
        digitos.remove("-")
    #Se remueve el punto de la lista
    digitos.remove(".")
    #Se convierte los elementos de la lista en enteros
    digitos : list = [int(digito) for digito in digitos]
    #Se mide la cantidad de elementos que tiene la lista
    num_digitos : int = len(digitos)
    #Se encuentra el número de digitos decimales
    num_decimales : int = num_digitos - ubicacion_decimal

    #Se separan los digitos decimales en una nueva lista
    digitos_decimales : list = []
    for i in range(num_decimales):
        digitos_decimales.append(digitos[ubicacion_decimal])
        ubicacion_decimal += 1

    #Se hallan los digitos enteros
    num_enteros : int = num_digitos-num_decimales
    digitos_enteros : list = []
    for j in range(num_enteros):
        digitos_enteros.append(digitos[j])

    #Se imprimen los arreglos
    print(f"Los digitos enteros del número son: {digitos_enteros}")
    print(f"Los digitos decimales del número son: {digitos_decimales}")
    return

def continuar():
    #El usuario decide si desea repetir el programa
    opcion : int = int(input("¿Desea continuar? Marque 1 (Sí) o 2 (No): "))
    return opcion

if __name__ == "__main__":
    #Inicia el programa
    print("Programa para separar los digitos de un número.")
    #El programa se va a repetir tantas veces el usuario desee
    while True:
        introducir()
        opcion : int = continuar()
        if opcion == 2:
            break
        elif opcion != 1 and 2:
            print("SintaxError")
            break

# ! /\|=\/ 
```

<table cellspacing="1" bgcolor="" align="center">
  <tr bgcolor="#252582">
    <th><b>Taller 2 - Parte 3</b></th>
  </tr>
  <tr bgcolor="#e4e4ed">
    <td style="color:#141414" align="center">Desarrollar un programa que permita ingresar dos números enteros y determinar si se tratan de números espejos. Definiendo números espejos como dos números a y b tales que a se lee de izquierda a derecha igual que se lee b de derecha a izquierda, y viceversa.</td>
  </tr>
  <tr bgcolor="#e4e4ed">
    <td style="color:#141414" align="center">En esta ocasión, se separan los digitos, luego se voltea uno de los números y se comparan si son números espejos.</td>
  </tr>
</table>

**Parte 3**
```python
#TALLER 2 - Parte 3
#Desarrollar un programa que permita ingresar dos números enteros y determinar si se tratan de números espejos.
#Definiendo números espejos como dos números a y b tales que a se lee de izquierda a derecha igual que se lee b de derecha a izquierda, y viceversa. 

def introducir():
    #Se introducen los números como flotantes
    num1 : float = float(input("Ingrese el número: "))
    num2 : float = float(input("Ingrese el número: "))
    #Se llama a la función para separar el número
    comparar_numeros(num1,num2)
    return

def comparar_numeros(num1 : float, num2 : float):
    #Se separan los digitos de los números
    digitos_numero_1 : list = separar_numero(num1)
    digitos_numero_2 : list = separar_numero(num2)
    #Se invierte el orden de la lista de num1
    digitos_invertidos : list = digitos_numero_1[::-1]
    #Se verifica si son números espejos
    if digitos_invertidos == digitos_numero_2:
        print(f"El número {num1} y el número {num2} son números espejos.")
        return
    else:
        print(f"El número {num1} y el número {num2} no son números espejos.")
        return

def separar_numero(num : float):
    #Se convierte al numero en una cadena
    numero : str = str(num)
    #Se separan los digitos
    digitos : list = [digito for digito in numero]
    #Si el número es menor a 0 se remueve el - de la lista
    if num < 0:
        digitos.remove("-")
    #Se remueve el punto de la lista
    digitos.remove(".")
    #Se convierte los elementos de la lista en enteros
    digitos_enteros : list = [int(digito) for digito in digitos]
    #Se elimina el cero que no fue ingresado por el usuario
    if digitos_enteros[-1] == 0:
        digitos_enteros.pop(-1)
    return digitos_enteros

def continuar():
    #El usuario decide si desea repetir el programa
    opcion : int = int(input("¿Desea continuar? Marque 1 (Sí) o 2 (No): "))
    return opcion

if __name__ == "__main__":
    #Inicia el programa
    print("Programa para determinar si dos números son números espejos.")
    #El programa se repetira tantas veces como el usuario lo desee
    while True:
        introducir()
        opcion : int = continuar()
        if opcion == 2:
            break
        elif opcion != 1 and 2:
            print("SintaxError")
            break

# ! /\|=\/ 
```

<table cellspacing="1" bgcolor="" align="center">
  <tr bgcolor="#252582">
    <th><b>Taller 2 - Parte 4</b></th>
  </tr>
  <tr bgcolor="#e4e4ed">
    <td style="color:#141414" align="center">Diseñar una función que permita calcular una aproximación de la función coseno alrededor de 0 para cualquier valor x (real), utilizando los primeros n términos de la serie de Maclaurin. Calcule con cuántos términos de la serie (i.e: cuáles valores de n), se tienen errores del 10%, 1%, 0.1% y 0.001%.</td>
  </tr>
  <tr bgcolor="#e4e4ed">
    <td style="color:#141414" align="center">Para este punto, se obtiene el valor real de la función importando el módulo math y luego se comparan los resultados con ayuda de varios bubles para calcular el número de términos de los errores.</td>
  </tr>
</table>

**Parte 4**
```python
#TALLER 2 - Punto 4
#Diseñar una función que permita calcular una aproximación de la función coseno alrededor de 0 para cualquier valor x (real), utilizando los primeros n términos de la serie de Maclaurin.

#Se importa math para conocer el valor real de la función
import math

def introducir():
    #Se ingresan las dos variables
    x : float = float(input("Ingrese el valor de x: "))
    n : int = int(input("Ingrese el número de términos a utilizar: "))
    desarrollo(x,n)

def desarrollo(x,n):
    maclaurin(x,n)
    #Se crean las tres variables como los resultados
    aprox : float
    v_real : float
    difer : float
    aprox, v_real, difer = maclaurin(x, n)
    print(f"Aproximación utilizando {n} términos de la serie de Maclaurin: {aprox}")
    print(f"Valor real de la función seno: {v_real}")
    print(f"Diferencia entre la aproximación y el valor real: {difer}")
    error_menor(x)

def maclaurin(x,n):
    #Se define la variable
    aproximacion : float = 0
     #Se repite el número de terminos a usar
    for i in range(n):
        a : int = factorial_numero(2*i)
        b : int = (x**(2*i))
        c : int = ((-1)**i)
        aproximacion += c*b/a
    #Se calcula el valor real
    valor_real : float = math.cos(x)
    #Se calcula la diferencia
    diferencia : float = valor_real - aproximacion
    #Se halla el valor absoluto de la ddiferencia
    diferencia_abs = diferencia if diferencia >= 0 else -diferencia
    return aproximacion, valor_real, diferencia_abs

def factorial_numero(i):
    #Se define la varibale que va a llevar el valor final
    factorial : int = 1
    #se repite i veces
    for j in range(1,i+1):
        factorial *= i
        i -=1
    return factorial

def error_menor(x):
    porcentaje_decimal : float = 0.00001
    for k in range(5):
        #Para calcular el número de terminos necesarios para que el error sea menor al 0.1%
        m : int = 0
        #Se halla el error máximo
        error = porcentaje_decimal * math.sin(x)
        #Se repite el ciclo hasta que la diferencia sea menor al error
        while True:
            aprox, v_real, difer = maclaurin(x, m)
            if difer < error:
                break
            m += 1
        porcentaje : float = porcentaje_decimal*100
        print(f"Para obtener menos del {porcentaje}% de error, se necesitan al menos {m} términos.")
        porcentaje_decimal *= 10
        
def continuar():
    #El usuario decide si deea repetir el código
    opcion : int = int(input("¿Desea continuar? Marque 1 (sí) o 2 (no): "))
    return opcion

if __name__ == "__main__":
    print("Programa para calcular una aproximación de la función seno alrededor de 0 para cualquier valor x (real), utilizando los primeros n términos de la serie de Maclaurin.")
    #El programa se repeitrá hasta que el usuario lo desee
    while True:
        introducir()
        opcion = continuar()
        if opcion == 2:
            break
        elif opcion != 1 and 2:
            print("Sintax error")
            break

# ! /\|=\/
```

<table cellspacing="1" bgcolor="" align="center">
  <tr bgcolor="#252582">
    <th><b>Taller 2 - Parte 5</b></th>
  </tr>
  <tr bgcolor="#e4e4ed">
    <td style="color:#141414" align="center">Desarrollar un programa que permita determinar el Minimo Comun Multiplo de dos numeros enteros. Abordar el problema desde una perpectiva tanto iterativa como recursiva. </td>
  </tr>
  <tr bgcolor="#e4e4ed">
    <td style="color:#141414" align="center">Para el quinto punto del taller, se obtiene el mínimo común múltiplo con ayuda del máximo común divisor.</td>
  </tr>
</table>

**Parte 5** 
```python
#TALLER 2 - Parte 5
#Desarrollar un programa que permita determinar el Minimo Comun Multiplo de dos numeros enteros. Abordar el problema desde una perpectiva tanto iterativa como recursiva. 

def introducir():
    #Se introducen los números como flotantes
    num1 : int = int(input("Ingrese el primer número: "))
    num2 : int = int(input("Ingrese el segundo número: "))
    #Se llama a la función para separar el número
    mcm(num1,num2)
    return

def mcm(num1:int,num2:int):
    #Se obtiene el máximo común divisor
    mcd_resultado : int = mcd(num1,num2)
    #Se obtiene el mínimo común múltiplo
    mcm_resultado : int = (num1*num2)/mcd_resultado
    #Se imprime el resultado
    print(f"El mínimo cómún múltiplo entre {num1} y {num2} es {mcm_resultado}")
    return

def mcd(num1:int,num2:int):
    # Algoritmo de Euclides para encontrar el MCD
    while num2 != 0:
        num1, num2 = num2, num1 % num2
    return num1

def continuar():
    #El usuario decide si desea repetir el programa
    opcion : int = int(input("¿Desea continuar? Marque 1 (Sí) o 2 (No): "))
    return opcion

if __name__ == "__main__":
    #Inicia el programa
    print("Programa para el mínimo común múltiplo entre dos números.")
    #El programa se repetira tantas veces como el usuario lo desee
    while True:
        introducir()
        opcion : int = continuar()
        if opcion == 2:
            break
        elif opcion != 1 and 2:
            print("SintaxError")
            break

# ! /\|=\/ 
```

<table cellspacing="1" bgcolor="" align="center">
  <tr bgcolor="#252582">
    <th><b>Taller 2 - Parte 6</b></th>
  </tr>
  <tr bgcolor="#e4e4ed">
    <td style="color:#141414" align="center">Desarrollar un programa que determine si en una lista existen o no elementos repetidos.</td>
  </tr>
  <tr bgcolor="#e4e4ed">
    <td style="color:#141414" align="center">Para este ejercicio, se considera una nueva lista en la que se van agregando los elementos ya evaluados y en caso de que el elemento ya exista dento de la nueva lista se considerara que la lista tiene elementos repetidos.</td>
  </tr>
</table>

**Parte 6** 
```python
#TALLER 2 - Parte 6
#Desarrollar un programa que determine si en una lista existen o no elementos repetidos.

def introducir():
    #Se introduce el número de elementos de la lista
    num_elementos : int = int(input("Ingrese el número de elementos del arreglo "))
    #Se crea la lista
    lista : list = []
    #Se añaden los elementos a la lista
    for i in range(num_elementos):
        lista.append([int(input(f"Ingrese el elemento {i}. Recuerde que solo son números naturales: "))])
    return lista

def desarrollo(lista : list):
    #Se crea una nueva lista para almacenar los elementos ya evaluados
    elementos_revisados : list = []
    for elemento in lista:
        if elemento in elementos_revisados:
            return True
        elementos_revisados.append(elemento)
    return False

def continuar():
    #El usuario decide si desea repetir el programa
    opcion : int = int(input("¿Desea continuar? Marque 1 (Sí) o 2 (No): "))
    return opcion

if __name__ == "__main__":
    #Inicia el programa
    print("Programa para saber si en una lista existen elementos repetidos.")
    #El programa se repetira tantas veces como el usuario lo desee
    while True:
        lista : list = introducir()
        desicion : bool = desarrollo(lista)
        if desicion == True:
            print("La lista tiene elementos repetidos")
        else:
            print("La lista no tiene elementos repetidos")
        opcion : int = continuar()
        if opcion == 2:
            break
        elif opcion != 1 and 2:
            print("SintaxError")
            break

# ! /\|=\/ 
```

<table cellspacing="1" bgcolor="" align="center">
  <tr bgcolor="#252582">
    <th><b>Taller 2 - Parte 7</b></th>
  </tr>
  <tr bgcolor="#e4e4ed">
    <td style="color:#141414" align="center">Desarrollar un programa que determine si en una lista se encuentra una cadena de caracteres con dos o más vocales. Si la cadena existe debe imprimirla y si no existe debe imprimir 'No existe'.</td>
  </tr>
  <tr bgcolor="#e4e4ed">
    <td style="color:#141414" align="center">En esta ocasión, se considera una nueva lista para las vovales y se verifica si existen elementos de la cadena que pertenezcan a la lista de las vocales.</td>
  </tr>
</table>

**Parte 7** 
```python
#TALLER 2 - Parte 7
"""
Desarrollar un programa que determine si en una lista se encuentra una cadena de caracteres con dos o más vocales.
Si la cadena existe debe imprimirla y si no existe debe imprimir 'No existe'.

"""

def introducir():
    #Se introduce el número de elementos de la lista
    num_elementos : int = int(input("Ingrese el número de elementos del arreglo: "))
    #Se crea la lista
    lista : list = []
    #Se añaden los elementos a la lista
    for i in range(num_elementos):
        lista.append(input(f"Ingrese el elemento {i}. Recuerde que solo son palabras: "))
    return lista,num_elementos

def desarrollo(lista : list, num_elementos : int):
    #Lista para almacenar las palabas que existen
    nueva_lista : list = []
    #Ciclo para evaluar todas las palabras
    for j in range(num_elementos):
        #Lista con los caracteres de una palabra
        caracteres : list = [caracter for caracter in lista[j]]
        #Se evaluan los caracteres
        condicion : bool = validar(caracteres)
        #A partir del resultado se condiciona pra entrar a la lista
        if condicion == True:
            nueva_lista.append(lista[j])
    #Se mide la longitud de la nueva lista
    longitud_nueva_lista : int = len(nueva_lista)
    #Se imprime la lista
    if longitud_nueva_lista != 0:
        print(nueva_lista)
    #Se imprime "No existe" en caso de que no hallan palabras con más de dos vocales
    else:
        print("No existe")

def validar(caracteres : list) -> bool:
    #Se consideran las vocales
    vocales : list = ["a","e","i","o","u"]
    vocales_revisadas : list = []
    #Se evalua cada uno de los caracteres
    for caracter in caracteres:
        if caracter in vocales:
            vocales_revisadas.append(caracter)
    #Se mide la cantidad de vocales que hay en la palabra
    num_vocales = len(vocales_revisadas)
    if num_vocales >= 2:
        return True
    else:
        return False

def continuar() -> int:
    #El usuario decide si desea repetir el programa
    opcion : int = int(input("¿Desea continuar? Marque 1 (Sí) o 2 (No): "))
    return opcion

if __name__ == "__main__":
    #Inicia el programa
    print("Programa conocer qué palabra tiene más de dos vocales.")
    #El programa se repetira tantas veces como el usuario lo desee
    while True:
        #Se inicia con el usuario decidieno si desea ingresar la lista por la consola o tomar la lista que está en el código
        tipo_lista : int = int(input(
            "Ingrese el tipo de lista que desea utilizar. Marque 1 (lista ingresada por consola) o 2(lista en código): "))
        #En caso de que la lista la ingrese por consola
        if tipo_lista == 1:
            lista : list = []  
            num_elementos : int = 0
            lista , num_elementos = introducir()
            desarrollo(lista,num_elementos)
        #En caso de que se quiera evaluar la lista que hay en el código
        elif tipo_lista == 2:
            lista1 : list = ["Hola","le","como","li","estas","la"]
            num_elementos = len(lista1)
            desarrollo(lista1,num_elementos)
        #En caso de que el usuario ingrese una opción no válida
        else:
            print("SintaxError")

        #El usuario decide si desea continuar
        opcion : int = continuar()
        if opcion == 2:
            break
        elif opcion != 1 and 2:
            print("SintaxError")
            break

# ! /\|=\/ 
```



<table cellspacing="1" bgcolor="" align="center">
  <tr bgcolor="#252582">
    <th><b>Taller 2 - Parte 8</b></th>
  </tr>
  <tr bgcolor="#e4e4ed">
    <td style="color:#141414" align="center">Desarrollar un programa que dadas dos listas determine que elementos tiene la primer lista que no tenga la segunda lista.</td>
  </tr>
  <tr bgcolor="#e4e4ed">
    <td style="color:#141414" align="center">En esta ocasión, se plantea un programa en la que exiten dos forma de evaluar las listas. La primera ingresada por la consola y la segunda con las listas que están en el programa. De esta manera, se crea una nueva lista para ir añadiendo los elementos que solo que encuentran en la primera lista.</td>
  </tr>
</table>

**Parte 8** 
```python
#TALLER 2 - Parte 8
#Desarrollar un programa que dadas dos listas determine que elementos tiene la primer lista que no tenga la segunda lista.

def introducir():
    #Se introduce el número de elementos de la lista 1
    num_elementos1 : int = int(input("Ingrese el número de elementos de la lista 1: "))
    #Se crea la lista
    lista1 : list = []
    #Se añaden los elementos a la lista
    for i in range(num_elementos1):
        lista1.append(input(f"Ingrese el elemento {i}. Recuerde que solo son palabras: "))

    #Se introduce el número de elementos de la lista 2
    num_elementos2 : int = int(input("Ingrese el número de elementos de la lista 2: "))
    #Se crea la lista
    lista2 : list = []
    #Se añaden los elementos a la lista
    for j in range(num_elementos2):
        lista2.append(input(f"Ingrese el elemento {i}. Recuerde que solo son palabras: "))
    return lista1,lista2

def desarrollo(lista1 : list, lista2 : list):
    #Lista para almacenar los elementos que no se repiten y las que sí
    lista_repetidos : list = []
    lista_unicos : list = []
    #Ciclo para evaluar todas las palabras
    for elemento in lista1:
        if elemento in lista2:
            lista_repetidos.append(elemento)
        else:
            lista_unicos.append(elemento)
    return lista_unicos

def continuar():
    #El usuario decide si desea repetir el programa
    opcion : int = int(input("¿Desea continuar? Marque 1 (Sí) o 2 (No): "))
    return opcion

if __name__ == "__main__":
    #Inicia el programa
    print("Programa para conocer los elementos que no están en una lista.")
    #El programa se repetira tantas veces como el usuario lo desee
    while True:
        #Se inicia con el usuario decidieno si desea ingresar la lista por la consola o tomar la lista que está en el código
        tipo_lista : int = int(input(
            "Ingrese el tipo de lista que desea utilizar. Marque 1 (lista ingresada por consola) o 2(lista en código): "))
        #En caso de que la lista la ingrese por consola
        if tipo_lista == 1:
            lista1 : list = []  
            lista2 : list = []
            lista_unicos : list = []  
            lista1,lista2 = introducir()
            lista_unicos = desarrollo(lista1,lista2)
            print(f"Los elementos únicos son: {lista_unicos}")

        #En caso de que se quiera evaluar la lista que hay en el código
        elif tipo_lista == 2:
            lista1 : list = ["Hola","le","como","li","estas","la"]
            lista2 : list = ["Hola","mundo","como","tierra","estas"]
            lista_unicos : list = []
            lista_unicos = desarrollo(lista1,lista2)
            print(f"Los elementos únicos son: {lista_unicos}")
        #En caso de que el usuario ingrese una opción no válida
        else:
            print("SintaxError")

        #El usuario deside si desea continuar
        opcion : int = continuar()
        if opcion == 2:
            break
        elif opcion != 1 and 2:
            print("SintaxError")
            break

# ! /\|=\/ 
```

<table cellspacing="1" bgcolor="" align="center">
  <tr bgcolor="#252582">
    <th><b>Taller 1 - Parte 9</b></th>
  </tr>
  <tr bgcolor="#e4e4ed">
  <td style="color:#141414" align="center">Escriba un programa que pida 5 números reales y calcule las siguientes operaciones:
        <li>El promedio</li>
        <li>La mediana</li>
        <li>El promedio multiplicativo </li>
        <li>Ordenar los números de forma ascendente</li>
        <li>Ordenar los números de forma descendente</li>
        <li>La potencia del mayor número elevado al menor número</li>
        <li>La raíz cúbica del menor número</li>
   </td>
  </tr>
  <tr bgcolor="#e4e4ed">
    <td style="color:#141414" align="center">Ahora, en el noveno punto del taller, se consideran los números como una lista y a partir dde allí se ejecutan las oeraciones.</td>
  </tr>
</table>

**Parte 9** 
```python
#Taller 2 - Parte 9
#Escriba un programa que pida 5 números reales y calcule las siguientes operaciones: 
#Promedio, mediana, promedio multiplicativo, ordenar los números de forma ascendente, ordenar los números de forma descendente, potencia del mayor número elevado al menor número, raíz cúbica del menor número.

def introducir() -> list:
    #Se introduce el número de elementos de la lista
    num_elementos : int = int(input("Ingrese el número de elementos de la lista: "))
    #Se crea la lista
    numeros : list = []
    #Se añaden los elementos a la lista
    for i in range(num_elementos):
        numeros.append(int(input(f"Ingrese el número. Recuerde que solo son números: ")))
    return numeros

def desarrollo(numeros : list):
    numeros.sort()

    promedio : float = 0
    for numero in numeros:
        promedio += (numero/5)
    print(f"Promedio: {promedio}")

    if len(numeros) % 2 == 0:
        mediana : float  = (numeros[len(numeros)//2-1] + numeros[len(numeros)//2])/2
    else:
        mediana = numeros[len(numeros)//2]
    print(f"Mediana: {mediana}")

    promedio_multiplicativo : float = 1
    for numero in numeros:
        promedio_multiplicativo *= numero
    promedio_multiplicativo = promedio_multiplicativo/(len(numeros))
    print(f"Promedio multiplicativo: {promedio_multiplicativo}")

    print(f"Números de forma ascendente: {numeros}")

    numeros.sort(reverse = True)
    print(f"Números de forma descendente: {numeros}")

    num_min : float = min(numeros)
    num_max : float = max(numeros)
    potencia : float = num_max**num_min
    print(f"potencia del mayor número elevado al menor número: {potencia}")

    raiz : float = num_min ** (1/3)
    print(f"La raiz cúbica del número menor: {raiz}")
    return

def continuar() -> int:
    #El usuario decide si desea repetir el programa
    opcion : int = int(input("¿Desea continuar? Marque 1 (sí) o 2 (no): "))
    return opcion

if __name__ == "__main__":
    #Inicia el programa
    print("Programa para conocer determinadas operaciones entre números.")
    #El programa se repetira tantas veces como el usuario lo desee
    while True:
        #Se ingresan los números
        numeros : list = introducir()
        #Se realizan las operaciones
        desarrollo(numeros)
        #El usuario decide si desea continuar
        opcion : int = continuar()
        if opcion == 2:
            break
        elif opcion != 1 and 2:
            print("Sintax error")
            break

# ! /\|=\/
```

<table cellspacing="1" bgcolor="" align="center">
  <tr bgcolor="#252582">
    <th><b>Taller 2 - Parte 10</b></th>
  </tr>
  <tr bgcolor="#e4e4ed">
    <td style="color:#141414" align="center">Desarrolle una función que, independientemente de los números que se encuentran en la lista A, 
tome aquellos números que son múltiplos de 3 y los guarde en una lista nueva, la cual debe ser retornada por la función.</td>
  </tr>
  <tr bgcolor="#e4e4ed">
    <td style="color:#141414" align="center">Para este ejercicio, se utilizan los dos métodos planteados:
      <li>El primero haciendo uso de la condición <i>numero % 3 == 0</i></li> 
      <li>El segundo se hace a partir de el criterio de divisibilidad, en donde se suman los digitos hasta que el número resultante sea un número de una cifra, con lo cual se valida la divisibilidad.</li>
    </td>
  </tr>
</table>

**Parte 10**
```python
#TALLER 2 - Parte 10
"""Suponga que se tiene una lista A con ciertos números enteros. 
Desarrolle una función que, independientemente de los números que se encuentran en la lista A, 
tome aquellos números que son múltiplos de 3 y los guarde en una lista nueva, la cual debe ser retornada por la función.
Implemente la perspectiva de un patrón de acumulación y también de comprensión de listas.
Desafío: Si ya lo logró, inténtelo ahora sin utilizar el módulo (%).
Pista: Un número es multiplo de 3 si la suma de sus dígitos también lo es, ¿verdad?
"""

def introducir() -> list:
    #Se introduce el número de elementos de la lista
    num_elementos : int = int(input("Ingrese el número de elementos de la lista: "))
    #Se crea la lista
    lista : list = []
    #Se añaden los elementos a la lista
    for i in range(num_elementos):
        lista.append(int(input(f"Ingrese el número. Recuerde que solo son números: ")))
    return lista

def desarrollo(lista : list):
    #Se ejecutan ambos métodos y se imprimen
    resultado_metodo1 : list = metodo_1(lista)
    resultado_metodo2 : list = metodo_2(lista)
    print(f"Resultado método 1: {resultado_metodo1}")
    print(f"Resultado método 2: {resultado_metodo2}")
    return

def metodo_1(lista : list) -> list:
    #Método con %
    multiplos : list = []
    #Se agregan a una nueva lista los que sí son múltiplos de tres
    for numero in lista:
        if numero % 3 == 0:
            multiplos.append(numero)
    return multiplos

def metodo_2(lista : list) -> list:
    #Método con el criterio de divisibilidad
    multiplos : list = []
    #Se agregan a una nueva lista los que sí son múltiplos de tres
    for numero in lista:
        numero_suma : int = numero
        while numero_suma > 0:
            #Se van sumando las cifras de los números
            numero_suma = suma_digitos(numero_suma)
            if numero_suma in [3,6,9]:
                multiplos.append(numero)
                break
            elif numero_suma in [1,2,4,5,7,8,0]:
                break
    return multiplos

def suma_digitos(numero : int) -> int:
    #Se suman las crifras del número
    numero : str = str(numero)
    suma_total : int = 0
    for digito in numero:
        suma_total += int(digito)
    return suma_total
 
def continuar() -> int:
    #El usuario decide si desea repetir el programa
    opcion : int = int(input("¿Desea continuar? Marque 1 (Sí) o 2 (No): "))
    return opcion

if __name__ == "__main__":
    #Inicia el programa
    print("Programa para conocer los multiplos de tres quenhay en un arreglo.")
    #El programa se repetira tantas veces como el usuario lo desee
    while True:
        #Se inicia con el usuario decidieno si desea ingresar la lista por la consola o tomar la lista que está en el código
        tipo_lista : int = int(input(
            "Ingrese el tipo de lista que desea utilizar. Marque 1 (lista ingresada por consola) o 2(lista en código): "))
        #En caso de que la lista la ingrese por consola
        if tipo_lista == 1:
            lista : list = []   
            lista = introducir()
            desarrollo(lista)

        #En caso de que se quiera evaluar la lista que hay en el código
        elif tipo_lista == 2:
            lista : list = [30,31,32,33,34,35,36,37,38,39,40]
            desarrollo(lista)

        #En caso de que el usuario ingrese una opción no válida
        else:
            print("SintaxError")

        #El usuario decide si desea continuar
        opcion : int = continuar()
        if opcion == 2:
            break
        elif opcion != 1 and 2:
            print("SintaxError")
            break

# ! /\|=\/ 
```

<table cellspacing="1" bgcolor="" align="center">
  <tr bgcolor="#252582">
    <th><b>Taller 2 - Parte 10</b></th>
  </tr>
  <tr bgcolor="#e4e4ed">
    <td style="color:#141414" align="center">Desarrollar un algoritmo que determine si una matriz es mágica. Se dice que una matriz cuadrada es mágica si la suma de cada una de sus filas, de cada una de sus columnas y de cada diagonal es igual.</td>
  </tr>
  <tr bgcolor="#e4e4ed">
    <td style="color:#141414" align="center">Para este ejercicio, se considera la matriz de dos formas, la primera ingresaada por la consola mientra que la segunda es la existente en el programa. Además, se elaboran distintas funciones para los siguientes procedimeintos: <i>Suma de cada fila, sumad e cada columna, suma de las dos diagonales e inprimir la matriz</i></td>
  </tr>
</table>

**Parte 10**
```python
#TALLER 2 - Parte 11
"""Desarrollar un algoritmo que determine si una matriz es mágica. 
Se dice que una matriz cuadrada es mágica si la suma de cada una de sus filas, 
de cada una de sus columnas y de cada diagonal es igual.
"""

def introducir():
    #Se introduce el número de elementos que tiene la fila
    num_elementos : int = int(input("Ingrese el número de elementos de las filas: "))
    #Se crea la matriz
    matriz : list = []

    #Se añaden los elementos a la lista
    for i in range(num_elementos):
        fila : list = []
        for j in range(num_elementos):
            fila.append(float(input(f"Ingrese el número de la fila {i+1} columna {j+1}: ")))
        matriz.append(fila)
    return matriz,num_elementos

def desarrollo(matriz : list, num_elementos : int):
    suma_fi, condicion_1 = suma_filas(matriz,num_elementos)
    suma_colum, condicion_2 = suma_columnas(matriz,num_elementos)
    suma_diag, condicion_3 = suma_diagonales(matriz,num_elementos)

    if condicion_1 == True and condicion_2 == True and condicion_3 == True:
        if suma_fi == suma_colum and suma_fi == suma_diag:
            print("La matriz es mágica.")
            #Se imprimime la matriz
            imprimir_matriz(matriz)
        else:
            print("La matriz no es mágica.")
            #Se imprimime la matriz
            imprimir_matriz(matriz)
    else:
        print("La matriz no es mágica.")
        #Se imprimime la matriz
        imprimir_matriz(matriz)

def imprimir_matriz(matriz):
    for fila in matriz:
        for elemento in fila:
            # Imprime el elemento seguido de una tabulación
            print(elemento, end="\t")
        # Imprime una nueva línea al final de cada fila
        print()
    return  

def suma_filas(matriz : list, num_elementos : int):
    suma_base : float = 0
    #Sumar los números de las filas
    for fila in matriz:
        suma_fila : float = 0
        #Sumar los elementos de cada fila
        for elemento in fila:
            suma_fila += elemento
        #Generar un total para lograr comparar los resultados
        suma_base += suma_fila
    suma_base = suma_base/num_elementos
    #Comparar las sumas.
    if suma_base == suma_fila:
        return suma_fila,True
    else:
        return suma_fila,False
    
def suma_columnas(matriz : list, num_elementos : int):
    suma_base : float = 0
    #Sumar los números de las columnas
    for columna in range(num_elementos):
        suma_columna : float = 0
        #Sumar los elementos de cada columna
        for fila in matriz:
            suma_columna += (fila[columna])        
        #Generar un total para lograr comparar los resultados
        suma_base += suma_columna
    suma_base = suma_base/num_elementos
    #Comparar las sumas.
    if suma_base == suma_columna:
        return suma_columna,True
    else:
        return suma_columna,False

def suma_diagonales(matriz : list, num_elementos : int):
    suma_diagonal_1 : float = 0
    suma_diagonal_2 : float = 0
    
    #Coordenadas
    a : int = 0
    b : int = 0
    #Sumar los números de la primera diagonal
    for elemento in range(num_elementos):
        suma_diagonal_1 += matriz[a][b]
        a += 1
        b += 1
    
    h : int = 0
    k : int = num_elementos-1
    for elemento in range(num_elementos):
        suma_diagonal_2 += matriz[h][k]
        h += 1
        k -= 1
    
    #Comparar las sumas.
    if suma_diagonal_1 == suma_diagonal_2:
        return suma_diagonal_1,True
    else:
        return suma_diagonal_1,False

def continuar() -> int:
    #El usuario decide si desea repetir el programa
    opcion : int = int(input("¿Desea continuar? Marque 1 (Sí) o 2 (No): "))
    return opcion

if __name__ == "__main__":
    #Inicia el programa
    print("Programa para conocer si una matriz es mágica.")
    #El programa se repetira tantas veces como el usuario lo desee
    while True:
        #Se inicia con el usuario decidieno si desea ingresar la matriz por la consola o tomar la matriz que está en el código
        tipo_lista : int = int(input(
            "Ingrese el tipo de matriz que desea utilizar. Marque 1 (lista ingresada por consola) o 2(lista en código): "))
        #En caso de que la lista la ingrese por consola
        if tipo_lista == 1:
            matriz : list = []   
            matriz,num_elementos = introducir()
            desarrollo(matriz,num_elementos)

        #En caso de que se quiera evaluar la lista que hay en el código
        elif tipo_lista == 2:
            #Cuadrado Mágico 7x7 con constante mágica de 175
            matriz : list = [
    [30, 39, 48, 1, 10, 19, 28],
    [38, 47, 7, 9, 18, 27, 29],
    [46, 6, 8, 17, 26, 35, 37],
    [5, 14, 16, 25, 34, 36, 45],
    [13, 15, 24, 33, 42, 44, 4],
    [21, 23, 32, 41, 43, 3, 12],
    [22, 31, 40, 49, 2, 11, 20]
]
            num_elementos : int = len(matriz[0])
            desarrollo(matriz,num_elementos)

        #En caso de que el usuario ingrese una opción no válida
        else:
            print("SintaxError")

        #El usuario decide si desea continuar
        opcion : int = continuar()
        if opcion == 2:
            break
        elif opcion != 1 and 2:
            print("SintaxError")
            break

# ! /\|=\/ 
```
