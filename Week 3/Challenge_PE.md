# **Guía de Aprendizaje: Implementación Progresiva de un Comecocos**

## **Introducción**
Esta guía está diseñada para que los aprendices implementen de forma progresiva un **Comecocos**, utilizando exclusivamente conceptos de **programación estructurada**. A lo largo de esta guía, se reforzará el uso de estructuras de control, modularización y manipulación de datos mediante el desarrollo del juego.

---

## **Sección 1 - Introducción a las librerías utilizadas**

### **1.1 Introducción a `pygame`**

`pygame` es una biblioteca de Python diseñada para desarrollar videojuegos. Facilita el manejo de gráficos, eventos del teclado, sonido y otros elementos clave para la interactividad en juegos.

#### **Funciones clave de `pygame`**
- `pygame.init()`: Inicializa todos los módulos de pygame.
- `pygame.display.set_mode((ancho, alto))`: Crea la ventana del juego.
- `pygame.draw.rect(superficie, color, (x, y, ancho, alto))`: Dibuja un rectángulo en la pantalla.
- `pygame.event.get()`: Captura eventos como pulsaciones de teclas o clics del ratón.
- `pygame.quit()`: Cierra pygame y finaliza el programa.

#### **Ejercicio 1: Crear una ventana con pygame**
```python
import pygame
pygame.init()

ANCHO, ALTO = 600, 400
pantalla = pygame.display.set_mode((ANCHO, ALTO))
pygame.display.set_caption("Mi primera ventana con pygame")

corriendo = True
while corriendo:
    for evento in pygame.event.get():
        if evento.type == pygame.QUIT:
            corriendo = False
    pantalla.fill((0, 0, 0))  # Fondo negro
    pygame.display.flip()

pygame.quit()
```

#### **Ejercicio 2: Dibujar un rectángulo y un círculo en la pantalla**
```python
import pygame
pygame.init()

ANCHO, ALTO = 600, 400
pantalla = pygame.display.set_mode((ANCHO, ALTO))

corriendo = True
while corriendo:
    for evento in pygame.event.get():
        if evento.type == pygame.QUIT:
            corriendo = False
    
    pantalla.fill((255, 255, 255))  # Fondo blanco
    pygame.draw.rect(pantalla, (0, 0, 255), (50, 50, 100, 100))  # Rectángulo azul
    pygame.draw.circle(pantalla, (255, 0, 0), (300, 200), 50)  # Círculo rojo
    pygame.display.flip()

pygame.quit()
```

#### **Ejercicio 3: Mover un cuadrado con las teclas del teclado**
```python
import pygame
pygame.init()

ANCHO, ALTO = 600, 400
pantalla = pygame.display.set_mode((ANCHO, ALTO))
pygame.display.set_caption("Mover un cuadrado")

x, y = 250, 150
velocidad = 5

corriendo = True
while corriendo:
    for evento in pygame.event.get():
        if evento.type == pygame.QUIT:
            corriendo = False
    
    teclas = pygame.key.get_pressed()
    if teclas[pygame.K_LEFT]:
        x -= velocidad
    if teclas[pygame.K_RIGHT]:
        x += velocidad
    if teclas[pygame.K_UP]:
        y -= velocidad
    if teclas[pygame.K_DOWN]:
        y += velocidad
    
    pantalla.fill((255, 255, 255))  # Fondo blanco
    pygame.draw.rect(pantalla, (0, 0, 255), (x, y, 50, 50))
    pygame.display.flip()

pygame.quit()
```

#### **Documentación Oficial de `pygame`**
[https://www.pygame.org/docs/](https://www.pygame.org/docs/)

---

### **1.2 Introducción a `tkinter`**

`tkinter` es la biblioteca gráfica de Python para la creación de interfaces de usuario. En este proyecto, se utilizará para mostrar mensajes emergentes.

#### **Funciones clave de `tkinter`**
- `tk.Tk()`: Crea la ventana principal.
- `messagebox.askyesno("Titulo", "Mensaje")`: Muestra una ventana de diálogo con opciones "Sí" o "No".
- `messagebox.showinfo("Titulo", "Mensaje")`: Muestra un mensaje informativo.

#### **Ejercicio 1: Mostrar un mensaje con `tkinter`**
```python
import tkinter as tk
from tkinter import messagebox

root = tk.Tk()
root.withdraw()  # Oculta la ventana principal

messagebox.showinfo("Bienvenida", "Este es un mensaje emergente con tkinter.")
```

#### **Ejercicio 2: Crear una ventana con un botón que muestra un mensaje**
```python
import tkinter as tk
from tkinter import messagebox

def mostrar_mensaje():
    messagebox.showinfo("Aviso", "Has presionado el botón")

root = tk.Tk()
root.title("Ventana con botón")

boton = tk.Button(root, text="Haz clic aquí", command=mostrar_mensaje)
boton.pack(pady=20)

root.mainloop()
```

#### **Ejercicio 3: Crear una ventana con dos botones de "Aceptar" y "Cancelar"**
```python
import tkinter as tk
from tkinter import messagebox

def aceptar():
    messagebox.showinfo("Resultado", "Has aceptado")

def cancelar():
    messagebox.showinfo("Resultado", "Has cancelado")

root = tk.Tk()
root.title("Opciones")

btn_aceptar = tk.Button(root, text="Aceptar", command=aceptar)
btn_aceptar.pack(side=tk.LEFT, padx=10, pady=20)

btn_cancelar = tk.Button(root, text="Cancelar", command=cancelar)
btn_cancelar.pack(side=tk.RIGHT, padx=10, pady=20)

root.mainloop()
```

#### **Documentación Oficial de `tkinter`**
[https://docs.python.org/3/library/tkinter.html](https://docs.python.org/3/library/tkinter.html)

---
## **Sección 2 - Código base con partes faltantes**

### **2.1 Importación de librerías y declaración de variables**
```python
import pygame
import random
import sys
import tkinter as tk
from tkinter import messagebox

# Inicializar pygame
pygame.init()

# Definir constantes
MAPA_ANCHO = 20
MAPA_ALTO = 9
ANCHO, ALTO = 1200, 800
TAMANO_CELDA = min(ANCHO // MAPA_ANCHO, ALTO // MAPA_ALTO)

pantalla = pygame.display.set_mode((MAPA_ANCHO * TAMANO_CELDA, MAPA_ALTO * TAMANO_CELDA))
pygame.display.set_caption("Comecocos")

# Definir colores
NEGRO = (0, 0, 0)
AZUL = (0, 0, 255)
AMARILLO = (255, 255, 0)
BLANCO = (255, 255, 255)
ROJO = (255, 0, 0)

# Definir variables del juego
pac_x, pac_y = 1, 1
fan_x, fan_y = 10, 5
puntos = 0
velocidad = 100
```

### **2.2 Código base con partes eliminadas**
```python
# Función para reiniciar el juego
def reiniciar_juego():
    """Restablece el estado del juego a sus valores iniciales."""
    global pac_x, pac_y, puntos
    # Reiniciar la posición del jugador a la coordenada inicial
    # Restablecer el puntaje a cero
    # Volver a cargar el mapa con sus elementos originales

# Función para mover el personaje principal
def mover_pacman(dx, dy):
    """Mueve el Pac-Man en la dirección dada y actualiza la recolección de puntos."""
    # Verificar que el movimiento no atraviese paredes
    # Si hay un punto en la nueva posición, incrementar el puntaje
    # Actualizar la posición del jugador en el mapa

# Función para mover el fantasma
def mover_fantasma():
    """Mueve el fantasma de forma aleatoria en direcciones permitidas."""
    # Seleccionar una dirección aleatoria entre arriba, abajo, izquierda o derecha
    # Comprobar que el movimiento no atraviese paredes
    # Actualizar la posición del fantasma en el mapa

# Función para mostrar la pantalla de Game Over
def mostrar_game_over():
    """Muestra la pantalla de Game Over y pregunta si el jugador quiere reiniciar."""
    # Dibujar el mensaje de Game Over en la pantalla
    # Esperar un tiempo y preguntar al usuario si desea reiniciar el juego

# Función para preguntar si el jugador quiere volver a jugar
def preguntar_volver_a_jugar(mensaje):
    """Muestra un cuadro de diálogo preguntando si el jugador quiere volver a jugar."""
    # Crear una ventana emergente con tkinter para mostrar un mensaje de juego terminado
    # Preguntar al usuario si desea jugar nuevamente con opciones "Sí" o "No"
    # Si el usuario elige "Sí", reiniciar el juego
    # Si el usuario elige "No", cerrar pygame y terminar el programa
```

### **2.3 Actividad para los estudiantes**
Los estudiantes deberán completar las funciones anteriores y la lógica del ciclo principal para que el juego funcione correctamente.

---

## **Sección 3 - Descripción del desafío**

En esta sección se describirá de manera clara el objetivo final del ejercicio y las tareas que los estudiantes deben realizar para completar el desarrollo del juego.

### **Objetivo del desafío**
Los estudiantes deberán implementar progresivamente las partes faltantes del código base para lograr un juego funcional de Comecocos. Durante el desarrollo, aplicarán conceptos de programación estructurada como:

- Control de flujo (condicionales y bucles).
- Modularización del código mediante funciones.
- Manipulación de estructuras de datos (listas y matrices).

### **Pasos a seguir**
1. **Comprender el código base**:
   - Revisar las funciones existentes y sus propósitos.
   - Identificar las partes del código que están incompletas.

2. **Implementar las funciones faltantes**:
   - Completar `reiniciar_juego()` para restablecer el estado del juego.
   - Implementar `mover_pacman(dx, dy)` asegurando la detección de colisiones.
   - Programar `mover_fantasma()` para generar movimientos aleatorios.
   - Crear la lógica de `mostrar_game_over()` y `preguntar_volver_a_jugar(mensaje)`.

3. **Ejecutar y probar el juego**:
   - Verificar que los movimientos y colisiones funcionen correctamente.
   - Realizar pruebas para asegurarse de que el juego termina correctamente y puede reiniciarse.

---
## **Sección 4 - Explicaciones teóricas de apoyo**

En esta sección se presentan los conceptos clave que los estudiantes deben comprender para completar la implementación del juego.

### **1. Control de flujo**

#### **Condicionales (`if`, `elif`, `else`)**
Las estructuras condicionales permiten ejecutar bloques de código en función de condiciones específicas. Ejemplo:
```python
x = 10
if x > 5:
    print("El número es mayor que 5")
elif x == 5:
    print("El número es 5")
else:
    print("El número es menor que 5")
```

#### **Bucles (`for`, `while`)**
Los bucles permiten repetir una acción varias veces. Ejemplo de un bucle `for`:
```python
for i in range(5):
    print("Iteración número:", i)
```
Ejemplo de un bucle `while`:
```python
contador = 0
while contador < 5:
    print("Contador:", contador)
    contador += 1
```

---

### **2. Funciones y modularización**

#### **Definición de funciones**
Las funciones permiten dividir el código en partes reutilizables. Ejemplo:
```python
def saludar(nombre):
    print(f"Hola, {nombre}!")

saludar("Carlos")
```

#### **Paso de parámetros y retorno de valores**
Las funciones pueden recibir valores de entrada y devolver resultados:
```python
def suma(a, b):
    return a + b

resultado = suma(5, 3)
print("La suma es:", resultado)
```

#### **Separación de responsabilidades**
Para mantener el código organizado, se recomienda dividir las funcionalidades en distintas funciones.

Ejemplo:
```python
def obtener_datos():
    return int(input("Ingresa un número: "))

def procesar_datos(numero):
    return numero * 2

def mostrar_resultado(resultado):
    print("El resultado es:", resultado)

num = obtener_datos()
res = procesar_datos(num)
mostrar_resultado(res)
```

---

### **3. Manipulación de estructuras de datos**

#### **Listas y matrices**
Las listas almacenan múltiples elementos en una sola variable:
```python
numeros = [1, 2, 3, 4, 5]
print(numeros[2])  # Imprime el tercer elemento (3)
```

Las matrices (listas de listas) permiten representar estructuras más complejas, como un mapa de juego:
```python
mapa = [
    [1, 1, 1, 1, 1],
    [1, 0, 0, 0, 1],
    [1, 0, 1, 0, 1],
    [1, 0, 0, 0, 1],
    [1, 1, 1, 1, 1]
]
print(mapa[1][2])  # Accede al elemento en la segunda fila y tercera columna
```

#### **Acceso y modificación de elementos en listas**
```python
numeros[2] = 99  # Modifica el tercer elemento de la lista
print(numeros)
```

Para modificar un valor en una matriz:
```python
mapa[1][2] = 9  # Cambia el valor en la segunda fila y tercera columna
```

---

### **4. Manejo de eventos en `pygame`**

#### **Captura de eventos (`pygame.event.get()`)**
Para detectar la interacción del usuario:
```python
for evento in pygame.event.get():
    if evento.type == pygame.QUIT:
        pygame.quit()
```

#### **Movimiento con el teclado**
```python
teclas = pygame.key.get_pressed()
if teclas[pygame.K_LEFT]:
    pac_x -= 1
elif teclas[pygame.K_RIGHT]:
    pac_x += 1
```

#### **Redibujado de la pantalla (`pygame.display.flip()`)**
Después de actualizar la lógica del juego, es necesario refrescar la pantalla:
```python
pygame.display.flip()
```
---

## **Sección 5 - Entregables esperados**

En esta sección se detallan los productos que los estudiantes deberán presentar al finalizar la actividad, como evidencia de su aprendizaje y aplicación de los conceptos trabajados en la implementación del Comecocos.

### **1. Código fuente del juego**
Los estudiantes deberán entregar el código fuente completo del juego, incluyendo:
- Implementación de todas las funciones definidas en el código base.
- Corrección de errores y depuración del código.
- Estructuración clara y organizada del código con comentarios explicativos.

### **2. Diagramas y documentación**
Los estudiantes deberán presentar documentación visual y escrita para demostrar su comprensión del flujo del programa:
- **Diagrama de bloques** que represente la estructura general del juego y la interacción entre sus componentes.
- **Diagrama de flujo** detallado de la lógica principal del juego, mostrando el proceso de movimiento del personaje, detección de colisiones y actualización de pantalla.
- **Explicación detallada** de todas las funciones implementadas en el código, indicando su propósito y funcionamiento.

#### **Ejemplo de una buena explicación detallada de código**

**Ejemplo: Explicación de una función para encontrar el número mayor en una lista**
```python
def encontrar_mayor(lista):
    """
    Encuentra el número mayor en una lista de valores numéricos.
    
    Parámetros:
        lista (list): Lista de números enteros o flotantes.
    
    Retorno:
        int/float: El número más grande dentro de la lista.
    
    Flujo de ejecución:
    1. Verifica si la lista está vacía; si lo está, devuelve None.
    2. Inicializa la variable `mayor` con el primer valor de la lista.
    3. Recorre la lista comparando cada elemento con `mayor`.
    4. Si encuentra un número más grande, actualiza `mayor`.
    5. Al finalizar el recorrido, devuelve el valor almacenado en `mayor`.
    """
    if not lista:
        return None
    
    mayor = lista[0]
    for numero in lista:
        if numero > mayor:
            mayor = numero
    
    return mayor
```

**Explicación:**
- La función `encontrar_mayor(lista)` recibe una lista de números como parámetro.
- Primero, verifica si la lista está vacía y retorna `None` en ese caso.
- Luego, inicializa la variable `mayor` con el primer número de la lista.
- A continuación, recorre la lista comparando cada número con `mayor`.
- Si encuentra un número más grande, actualiza el valor de `mayor`.
- Finalmente, devuelve el número mayor encontrado en la lista.

Este nivel de detalle debe mantenerse en la explicación de todas las funciones implementadas.

### **3. Análisis de ejecución y pruebas**
Los estudiantes deberán realizar pruebas funcionales para garantizar que el juego opera correctamente. Deberán presentar:
- **Casos de prueba** documentados, describiendo escenarios específicos y sus resultados esperados.
- **Registro de errores detectados y soluciones aplicadas**, detallando cómo se resolvieron los problemas encontrados durante el desarrollo.
- **Evidencia visual** en forma de capturas de pantalla o un breve video mostrando el juego en ejecución.

### **4. Reflexión y mejoras propuestas**
Como parte del aprendizaje, los estudiantes deberán realizar una reflexión final en la que aborden:
- **Dificultades encontradas** y cómo fueron superadas.
- **Aspectos que mejorarían en el código** si tuvieran más tiempo o experiencia.
- **Posibles mejoras al juego**, como agregar niveles, más enemigos o nuevos desafíos.

---

Con estos entregables, se espera que los estudiantes no solo completen la implementación del Comecocos, sino que también desarrollen habilidades de documentación, prueba y análisis de código.

---

## **Sección 6 - Modularización del código**

La modularización del código es una estrategia clave en la programación estructurada que permite dividir un programa en funciones reutilizables y organizadas de manera lógica. En el desarrollo del Comecocos, aplicar este enfoque facilitará la comprensión, depuración y mantenimiento del código.

### **1. ¿Por qué es importante modularizar el código?**
- **Facilita la reutilización**: Permite escribir funciones que pueden ser llamadas múltiples veces sin duplicar código.
- **Mejora la organización**: Separa la lógica en secciones bien definidas, facilitando su comprensión y mantenimiento.
- **Facilita la depuración**: Al dividir el código en módulos, los errores pueden identificarse y corregirse más rápidamente.
- **Aumenta la legibilidad**: Un código modular es más fácil de leer y entender, lo que mejora la colaboración en proyectos grupales.

### **2. Identificación de módulos en el juego**
Para mejorar la estructura del código, se pueden dividir las funcionalidades del Comecocos en módulos separados, por ejemplo:

- **Módulo de configuración**: Define constantes y parámetros del juego, como colores, dimensiones y velocidad.
- **Módulo de inicialización**: Configura los valores iniciales y estructuras de datos, como el estado del mapa y la posición del personaje.
- **Módulo de lógica del juego**: Contiene las funciones que definen el comportamiento del jugador y los enemigos.
- **Módulo de renderizado**: Se encarga de actualizar la pantalla y dibujar los elementos visuales del juego.
- **Módulo de manejo de eventos**: Captura y procesa las entradas del usuario, como teclas presionadas o cierre de la ventana.

### **3. Estrategia para modularizar el código**
Para aplicar la modularización correctamente, los estudiantes deben:
1. **Identificar las secciones principales del código** y agrupar las líneas de código relacionadas dentro de funciones.
2. **Evitar el uso excesivo de variables globales**, pasando datos a las funciones como parámetros para mejorar la encapsulación.
3. **Separar la lógica del juego de la parte gráfica**, asegurando que las funciones de actualización del estado del juego no dependan directamente de las funciones de dibujo en la pantalla.
4. **Nombrar las funciones de manera clara y descriptiva**, de modo que cada una indique explícitamente su propósito.

### **4. Actividad para los estudiantes**
Los estudiantes deberán:
1. **Identificar posibles módulos en el código del Comecocos**.
2. **Separar la lógica en funciones específicas**, asegurando que cada función cumpla con una sola responsabilidad.
3. **Refactorizar su código** para mejorar la organización y legibilidad.
4. **Explicar cómo la modularización mejoró su código** en un breve informe, detallando los cambios realizados y sus beneficios.

---

Al modularizar el código del Comecocos, los estudiantes aprenderán a estructurar mejor sus proyectos y a escribir programas más organizados y fáciles de mantener.

---

## **Sección 7 - Creación de una aplicación ejecutable sin Python instalado**

Para compartir el juego Comecocos con otros usuarios que no tengan Python instalado en sus computadoras, es necesario convertir el código fuente en un ejecutable. Esto permitirá que el juego pueda ejecutarse en cualquier equipo sin depender de la instalación de Python o de sus librerías.

### **1. Herramientas para generar un ejecutable**
Existen diversas herramientas que permiten empaquetar una aplicación de Python en un archivo ejecutable. Algunas de las más utilizadas son:
- **`pyinstaller`**: Permite generar un ejecutable compatible con Windows, macOS y Linux.
- **`cx_Freeze`**: Alternativa a `pyinstaller`, enfocada en aplicaciones con interfaz gráfica.
- **`auto-py-to-exe`**: Interfaz gráfica que simplifica el uso de `pyinstaller`.

### **2. Pasos para generar el ejecutable con `pyinstaller`**
1. **Instalar `pyinstaller`**:
   - En la terminal o consola de comandos, ejecutar:
     ```sh
     pip install pyinstaller
     ```

2. **Ubicar el archivo principal del juego**:
   - Asegurarse de que el archivo principal (`come-cocos.py`) esté en la carpeta del proyecto.

3. **Generar el ejecutable**:
   - En la terminal, dentro de la carpeta del proyecto, ejecutar:
     ```sh
     pyinstaller --onefile --windowed come-cocos.py
     ```
   - La opción `--onefile` crea un solo archivo `.exe`.
   - La opción `--windowed` evita que se abra la consola al ejecutar el programa (recomendado para aplicaciones gráficas).

4. **Ubicar el ejecutable generado**:
   - Una vez finalizado el proceso, el ejecutable estará en la carpeta `dist/` dentro del proyecto.

5. **Probar el ejecutable en otro equipo**:
   - Copiar el archivo generado y ejecutarlo en una computadora sin Python instalado para verificar su correcto funcionamiento.

### **3. Consideraciones al distribuir el ejecutable**
- **Compatibilidad**: Los ejecutables generados en Windows no funcionarán en macOS o Linux (y viceversa). Para compartir el juego en otros sistemas operativos, se debe compilar en cada uno de ellos.
- **Archivos adicionales**: Si el juego usa imágenes, sonidos u otros recursos externos, estos deben incluirse en el mismo directorio que el ejecutable o empaquetarse dentro del mismo.
- **Errores y dependencias**: Si el ejecutable no funciona, revisar las dependencias del juego y asegurarse de que todas las librerías necesarias estén correctamente instaladas.

### **4. Actividad para los estudiantes**
Los estudiantes deberán:
1. **Generar un ejecutable de su juego usando `pyinstaller`**.
2. **Probar el ejecutable en otra computadora sin Python instalado** y documentar el proceso.
3. **Identificar posibles errores y soluciones al empaquetar su aplicación**.

---

Este proceso permitirá a los estudiantes comprender cómo distribuir sus aplicaciones sin depender del entorno de desarrollo de Python, asegurando que su juego pueda ser ejecutado por cualquier usuario.

Con esto, la guía de aprendizaje queda completa y lista para ser utilizada en el desarrollo del Comecocos. 🎮



















