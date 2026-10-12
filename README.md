<div align="center">

# INSTITUTO TECNOLÓGICO SUPERIOR SUDAMERICANO

<br>

**AUTOR:** KEVIN ALEXIS PATIÑO MUÑOZ

**MATERIA:** TENDENCIAS TECNOLÓGICAS

**DOCENTE:** ING. MARCO AURELIO GUAMÁN BUESTÁN

**CURSO:** 3RO.

**CARRERA:** “DESARROLLO DE SOFTWARE”

**TEMA:** TAREA AUTÓNOMA SEMANA 1 – COMANDOS DE LINUX

**FECHA DE ELABORACIÓN:** 12/10/2026

**FECHA DE ENTREGA:** 13/10/2026

<br><br>

**CUENCA - ECUADOR**

**2026**

</div>

---

## 1. Título

**Práctica No. 1: Creación y manipulación de archivos y directorios con comandos de Linux**

## 2. Tiempo de duración

60 minutos.

## 3. Fundamentos

Linux es un sistema operativo de tipo Unix, libre y de código abierto. Aunque hoy cuenta con entornos gráficos muy completos, la forma más directa y eficiente de trabajar con él sigue siendo la **terminal** o línea de comandos. Desde ella se ejecuta un programa llamado **shell** (intérprete de comandos), siendo **Bash** (*Bourne Again SHell*) el más utilizado. El shell recibe las órdenes que escribe el usuario, las interpreta y le pide al sistema operativo que las ejecute.

En Windows es posible trabajar con estos comandos mediante **Git Bash**, que incluye un entorno Bash con las utilidades básicas de GNU, o mediante **WSL (Windows Subsystem for Linux)**, que permite ejecutar una distribución real de Linux, como Ubuntu, dentro de Windows.

**Sistema de archivos.** En Linux todo se organiza en un árbol jerárquico que parte de la raíz `/`. Cada usuario tiene un directorio personal (`~`). Las rutas pueden ser **absolutas**, cuando empiezan desde la raíz (`/home/usuario/proyecto`), o **relativas**, cuando parten del directorio actual (`../scripts`). El punto `.` representa el directorio actual y los dos puntos `..` el directorio padre.

**Comandos básicos de navegación y gestión:**

| Comando | Función |
|---------|---------|
| `pwd` | Muestra la ruta del directorio actual |
| `ls` | Lista el contenido de un directorio (`-l` formato largo, `-R` recursivo) |
| `cd` | Cambia de directorio |
| `mkdir` | Crea directorios |
| `touch` | Crea un archivo vacío o actualiza su fecha de modificación |
| `cat` | Muestra o concatena el contenido de archivos |
| `echo` | Imprime texto en la salida estándar |
| `cp` | Copia archivos o directorios |
| `mv` | Mueve o renombra archivos |
| `rm` | Elimina archivos |
| `rmdir` | Elimina directorios **solo si están vacíos** |
| `history` | Muestra el historial de comandos ejecutados |

**Flujos estándar y redirección.** Todo programa en Linux trabaja con tres flujos: entrada estándar (`stdin`, 0), salida estándar (`stdout`, 1) y salida de errores (`stderr`, 2). La **redirección** permite cambiar el destino de esos flujos:

- `>` envía la salida a un archivo y **sobrescribe** su contenido.
- `>>` envía la salida a un archivo y **añade** el contenido al final, sin borrar lo existente.
- `<` toma la entrada desde un archivo.

**Tuberías (pipes).** El operador `|` conecta la salida estándar de un comando con la entrada estándar de otro, lo que permite encadenar herramientas pequeñas para resolver tareas más grandes. Por ejemplo, `history | cat > archivo.txt` envía el historial a `cat`, y su salida se redirige a un archivo. Esta filosofía de “programas pequeños que hacen una sola cosa bien y se combinan entre sí” es una de las bases de Unix.

Dominar estos comandos es fundamental para un desarrollador de software, porque los servidores, los contenedores (Docker), los pipelines de integración continua y gran parte de las herramientas de desarrollo funcionan sobre Linux y se administran desde la terminal.

## 4. Conocimientos previos

- Manejo básico del sistema operativo Windows y de su explorador de archivos.
- Concepto de archivo, carpeta y ruta.
- Uso básico de la terminal (abrir Git Bash o Ubuntu WSL).
- Uso básico de Git y GitHub para subir un repositorio.

## 5. Objetivos

- Crear una estructura de directorios desde la terminal con `mkdir`.
- Crear, copiar, renombrar y mover archivos con `touch`, `echo`, `cp` y `mv`.
- Aplicar redirección (`>` y `>>`) para escribir y concatenar contenido en archivos.
- Eliminar archivos y directorios vacíos con `rm` y `rmdir`.
- Usar tuberías (`|`) para guardar el historial de comandos en un archivo.

## 6. Equipo necesario

- Computador con sistema operativo Windows 10/11 (también válido Linux o macOS).
- Git Bash (Git for Windows 2.x) o Ubuntu en WSL 2.
- Cuenta de GitHub.
- Conexión a internet.

## 7. Material de apoyo

- Guía de la asignatura Tendencias Tecnológicas.
- Plantilla del informe: <https://github.com/maguaman2/informe-tendencias>
- Manual de GNU Bash: <https://www.gnu.org/software/bash/manual/>
- Cheat sheet de comandos Linux.

## 8. Procedimiento

### 8.1 Crear la estructura de carpetas

Se verifica el directorio de trabajo, se crea la carpeta `proyecto_comandos` y dentro de ella las subcarpetas `documentos`, `imagenes` y `scripts`.

```bash
pwd
mkdir proyecto_comandos
cd proyecto_comandos
mkdir documentos imagenes scripts
ls -l
```

**Figura 1.** Estructura de carpetas creada

```text
total 0
drwxr-xr-x 1 kevin 197609 0 Oct 12 11:53 documentos
drwxr-xr-x 1 kevin 197609 0 Oct 12 11:53 imagenes
drwxr-xr-x 1 kevin 197609 0 Oct 12 11:53 scripts
```

### 8.2 Manipulación de archivos

Dentro de `documentos` se crea `notas.txt` y se le agregan tres líneas con `echo` y redirección. La primera línea usa `>` y las siguientes `>>` para no sobrescribir.

```bash
cd documentos
touch notas.txt
echo "Linea 1: Practica de comandos Linux en Git Bash" > notas.txt
echo "Linea 2: Aprendiendo a crear, copiar y mover archivos" >> notas.txt
echo "Linea 3: Redireccion y tuberias en la terminal" >> notas.txt
cat notas.txt
```

**Figura 2.** Contenido de `notas.txt`

```text
Linea 1: Practica de comandos Linux en Git Bash
Linea 2: Aprendiendo a crear, copiar y mover archivos
Linea 3: Redireccion y tuberias en la terminal
```

Se copia `notas.txt` a la carpeta `scripts` con el nombre `backup_notas.txt` (copia y renombrado en un solo paso), y luego se mueve a `imagenes`.

```bash
cp notas.txt ../scripts/backup_notas.txt
ls ../scripts
mv ../scripts/backup_notas.txt ../imagenes/
ls ../scripts ../imagenes
```

**Figura 3.** El respaldo ya no está en `scripts`, ahora está en `imagenes`

```text
../imagenes:
backup_notas.txt

../scripts:
```

### 8.3 Redirección y concatenación

Se crea `resumen.txt`, se redirecciona el contenido de `notas.txt` hacia él con `>` y luego se añade una línea nueva con `>>`, sin sobrescribir.

```bash
touch resumen.txt
cat notas.txt > resumen.txt
echo "Linea 4: Linea agregada con >> sin sobrescribir" >> resumen.txt
cat resumen.txt
```

**Figura 4.** Contenido de `resumen.txt`

```text
Linea 1: Practica de comandos Linux en Git Bash
Linea 2: Aprendiendo a crear, copiar y mover archivos
Linea 3: Redireccion y tuberias en la terminal
Linea 4: Linea agregada con >> sin sobrescribir
```

### 8.4 Eliminación de archivos y carpetas

Se elimina `backup_notas.txt` y, como la carpeta `imagenes` queda vacía, se borra con `rmdir` (este comando falla si la carpeta tiene contenido, lo que evita borrar información por error).

```bash
rm ../imagenes/backup_notas.txt
rmdir ../imagenes
cd ..
ls -R
```

**Figura 5.** Estructura final sin la carpeta `imagenes`

```text
.:
documentos
scripts

./documentos:
notas.txt
resumen.txt

./scripts:
```

### 8.5 Entrega: historial con tuberías

Se vuelca el historial de comandos al archivo `tarea-s1-kevin_patino.txt` usando una tubería.

```bash
history | cat > ../tarea-s1-kevin_patino.txt
```

El archivo resultante está en la raíz de este repositorio: [`tarea-s1-kevin_patino.txt`](tarea-s1-kevin_patino.txt).

## 9. Resultados esperados

Al finalizar la práctica se obtuvo:

- La carpeta `proyecto_comandos` con las subcarpetas `documentos` y `scripts` (la carpeta `imagenes` fue eliminada al quedar vacía).
- El archivo `documentos/notas.txt` con tres líneas de texto.
- El archivo `documentos/resumen.txt` con el contenido de `notas.txt` más una cuarta línea añadida con `>>`.
- El archivo `tarea-s1-kevin_patino.txt` con el historial completo de los comandos ejecutados, generado mediante tubería.

Estructura final del repositorio:

```text
tarea-s1-comandos-linux/
├── README.md
├── tarea-s1-kevin_patino.txt
└── proyecto_comandos/
    ├── documentos/
    │   ├── notas.txt
    │   └── resumen.txt
    └── scripts/
```

Con esto se comprobó la diferencia entre `>` (sobrescribe) y `>>` (añade), que `cp` puede copiar y renombrar en un solo paso, que `mv` mueve archivos entre carpetas y que `rmdir` solo elimina directorios vacíos.

## 10. Bibliografía

- Free Software Foundation. (2022). *GNU Bash reference manual*. <https://www.gnu.org/software/bash/manual/>
- Shotts, W. (2019). *The Linux command line: A complete introduction* (2.ª ed.). No Starch Press.
- Git for Windows. (2026). *Git for Windows*. <https://gitforwindows.org/>
- Microsoft. (2025). *¿Qué es el Subsistema de Windows para Linux?* Microsoft Learn. <https://learn.microsoft.com/es-es/windows/wsl/about>
