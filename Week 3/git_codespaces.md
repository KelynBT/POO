# **Guía de Aprendizaje: GitHub Básico y Codespaces**

## **Introducción**
GitHub es una plataforma que permite gestionar proyectos de desarrollo de software utilizando control de versiones con Git. Puede usarse como un espacio personal para almacenar y organizar archivos, colaborar en proyectos y desarrollar software de manera estructurada.

GitHub Codespaces es un entorno de desarrollo en la nube que permite ejecutar y editar código directamente desde el navegador, sin necesidad de configuraciones locales. Esto facilita la programación en cualquier dispositivo con conexión a internet.

---

## **Sección 1 - Creación de una Cuenta y Configuración Básica**

### **1.1 Creación de una cuenta en GitHub**
1. Visita [GitHub](https://github.com/).
2. Haz clic en "Sign up" y completa los datos: nombre de usuario, correo y contraseña.
3. Verifica tu correo electrónico y configura la autenticación en dos pasos para mayor seguridad.

### **1.2 Instalación y Configuración de Git (Opcional)**
Si deseas usar Git en tu equipo antes de trabajar con Codespaces:
1. Descarga Git desde [git-scm.com](https://git-scm.com/downloads).
2. Instálalo siguiendo las instrucciones según tu sistema operativo.
3. Configura Git con:
   ```sh
   git config --global user.name "Tu Nombre"
   git config --global user.email "tuemail@example.com"
   ```

### **1.3 Creación de un Repositorio**
1. Inicia sesión en GitHub y haz clic en el botón "New repository".
2. Asigna un nombre, descripción y decide si será público o privado.
3. Selecciona "Add a README file" y haz clic en "Create repository".

---

## **Sección 2 - Introducción a GitHub Codespaces**

### **2.1 ¿Qué es Codespaces y por qué usarlo?**
Codespaces es un entorno de desarrollo en la nube que permite ejecutar código sin necesidad de instalar dependencias en tu equipo.

### **2.2 Habilitación de Codespaces en un Repositorio**
1. Abre un repositorio en GitHub.
2. Haz clic en la pestaña "Code" y selecciona la opción "Codespaces".
3. Activa Codespaces si es necesario.

### **2.3 Creación de un Codespace y Primera Ejecución**
1. En la pestaña "Codespaces", haz clic en "New codespace".
2. Espera a que el entorno se cargue.
3. Abre el terminal integrado y ejecuta:
   ```sh
   echo "Hola, Codespaces!" > hola.txt
   cat hola.txt
   ```

---

## **Sección 3 - Gestión de Archivos en GitHub con Codespaces**

### **3.1 Creación y Edición de Archivos**
1. En Codespaces, haz clic en "New File" y asigna un nombre.
2. Escribe contenido y guarda con `Ctrl + S`.

### **3.2 Uso del Terminal de Codespaces**
El terminal permite ejecutar comandos de Git:
```sh
git status
git add .
git commit -m "Primer commit"
```

### **3.3 Realización de Commits y Sincronización con el Repositorio**
1. Usa `git add .` para agregar archivos al commit.
2. Ejecuta `git commit -m "Mensaje descriptivo"`.
3. Sube los cambios con `git push`.

---

## **Sección 4 - Organización del Repositorio**

### **4.1 Uso de Carpetas y Archivos README**
1. Crea carpetas para organizar archivos.
2. Agrega un archivo `README.md` con información del proyecto.

### **4.2 Creación de Ramas y Fusión de Cambios**
1. Crea una rama con:
   ```sh
   git checkout -b nueva-rama
   ```
2. Fusiona cambios con:
   ```sh
   git checkout main
   git merge nueva-rama
   ```

---

## **Sección 5 - Compartir y Colaborar en GitHub (Opcional)**

### **5.1 Configuración de Permisos y Colaboradores**
1. Ve a "Settings" → "Manage access".
2. Agrega colaboradores con permisos de lectura o escritura.

### **5.2 Issues y Tableros de Proyectos (Opcional)**
- Los Issues ayudan a gestionar tareas y errores.
- Los tableros permiten organizar proyectos con metodología Kanban.

---

## **Sección 6 - Creación de un Proyecto de Prueba**
1. **Crear un repositorio**: Ve a GitHub, haz clic en "New repository" y asigna el nombre `mi-proyecto`.
2. **Abrir Codespaces**: Accede al repositorio y haz clic en "Code" → "Codespaces" → "Create codespace on main".
3. **Crear un archivo de código**:
   - En el explorador de archivos de Codespaces, haz clic en "New File".
   - Nombra el archivo `script.py` y escribe el siguiente código:
   ```python
   print("Hola, GitHub Codespaces!")
   ```
   - Guarda los cambios con `Ctrl + S`.
4. **Ejecutar el código**:
   - Abre el terminal integrado en Codespaces.
   - Ejecuta el archivo con:
     ```sh
     python script.py
     ```
   - Debería aparecer el mensaje `Hola, GitHub Codespaces!` en la terminal.
5. **Modificar el archivo existente**:
   - Abre `script.py` en el editor.
   - Modifica el contenido para que imprima un mensaje diferente, por ejemplo:
   ```python
   print("¡Hola, este es mi primer cambio en GitHub Codespaces!")
   ```
   - Guarda los cambios (`Ctrl + S`).
6. **Hacer commit y subir cambios**:
   - Agregar los cambios:
     ```sh
     git add .
     ```
   - Crear un commit con un mensaje descriptivo:
     ```sh
     git commit -m "Modificación del script de prueba"
     ```
   - Subir cambios al repositorio:
     ```sh
     git push
     ```
7. **Verificar en GitHub**:
   - Regresa a GitHub y abre el repositorio `mi-proyecto`.
   - Verifica que `script.py` se haya actualizado correctamente.

---

## **Sección 7 - Buenas Prácticas en GitHub**
1. Usa nombres descriptivos en commits.
2. Mantén un `README.md` actualizado.
3. Usa ramas para trabajar en nuevas funcionalidades.
4. Mantén un orden en la estructura del repositorio.

---

## **Recursos Adicionales**
- [Documentación Oficial de GitHub](https://docs.github.com/)
- [Documentación de Codespaces](https://docs.github.com/en/codespaces)
- [Aprende Git con ejercicios interactivos](https://learngitbranching.js.org/)

---

¡Felicidades! Ahora tienes un conocimiento básico de GitHub y Codespaces para gestionar tus proyectos de manera eficiente.
