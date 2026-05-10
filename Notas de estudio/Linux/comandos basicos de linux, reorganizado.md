# 🐧 Linux & Cybersecurity Mastery Vault

> [!QUOTE] ESTADO DE DOMINIO
> El desorden es debilidad. Esta es tu base de conocimientos sin filtros. Cada comando es una herramienta; cada flag es una ventaja. No aceptes menos que la excelencia técnica.

---

## 📂 1. Navegación y Gestión de Archivos

| Comando | Acción | Descripción Técnica |
| :--- | :--- | :--- |
| `pwd` | Localización | Muestra dónde está localizado el usuario. ![[Pasted image 20260316133823.png]] |
| `ls` | Listar | Muestra los archivos del directorio actual. ![[Pasted image 20260316134016.png]] |
| `cd` | Cambiar | Cambia de directorio. `cd ..` sale a la carpeta anterior. ![[Pasted image 20260316134047.png]] |
| `mkdir` | Directorios | Crea directorios. `-p` crea rutas completas aunque no existan los padres. ![[Pasted image 20260321105358.png]] |
| `rm` | Eliminar | `rm [archivo]`. Para ficheros/directorios usa `-r`. Sin subruta, elimina todo el contenido. ![[Pasted image 20260321105503.png]] |
| `mv` | Mover/Renombrar | Mueve archivos a rutas (preferiblemente absolutas) o renombra: `mv [orig] [edit]`. ![[Pasted image 20260321110612.png]] ![[Pasted image 20260321110943.png]] ![[Pasted image 20260321111332.png]] |

### 💡 Lógica de Rutas y Atajos
* **Ruta Absoluta:** Trazado desde el directorio raíz `/`. Ejemplo: `/home/carpeta1/carpeta2`. Siempre inicia con `/`.
* **Ruta Relativa:** Trazado desde el directorio actual. Ejemplo: `carpeta2/archivo.txt`.
* **Multinivel:** `cd ../../../` para retroceder múltiples carpetas (cada `..` es un nivel).
* **Nombres con Espacios:** Obligatorio usar comillas dobles: `"Nombre con Espacio"`. ![[Pasted image 20260316141845.png]]
* **Control de Cursores:** * `CTRL + R`: Búsqueda recursiva de instrucciones previas.
    * `history`: Muestra el historial de instrucciones.
    * `! [numero]`: Ejecuta la instrucción específica del historial.

---

## 📝 2. Manipulación de Texto y Archivos

### 🔹 Creación y Edición
* **Archivos:** `cat` o `touch` crean archivos. Con `nano` ingresas al editor de texto.
* **Echo:** Permite escribir antes de crear el archivo. 
    * `echo "Hola mundo" > practica.txt`. ![[Pasted image 20260316134601.png]]
* **Man:** `man [comando]` brinda la guía oficial del comando.

### 🔹 Procesamiento de Datos (Data Wrangling)
* **sort:** Ordena el contenido de un texto.
    * `-n`: Numérico.
    * `-r`: Inverso.
    * `-u`: Elimina duplicados: `sort -u archivo.txt > sin_duplicados.txt`.
    * `-k [col]`: Ordena por columnas específicas (ej. filtrar por edad).
* **uniq:** Elimina líneas duplicadas (requiere `sort` previo).
    * `-c`: Cuenta ocurrencias.
    * `-d`: Solo muestra las duplicadas.
    * `-u`: Solo muestra las únicas.
    * `-i`: Ignora mayúsculas/minúsculas.
* **strings:** Busca caracteres imprimibles en archivos binarios (`.bin`).
* **tr (Translate):** Reemplazo y eliminación.
    * `-d`: Eliminar caracteres.
    * `-s`: Squeeze (elimina duplicados repetidos).
    * **Caso ROT13:** `tr 'A-Za-z' 'N-ZA-Mn-za-m'` (Sustituye 13 posiciones en el alfabeto).
* **cat (Avanzado):**
    * Concatenar: `cat f1 f2 > unido.txt`.
    * Añadir: `cat nueva_data >> f1`.
    * `-n`: Enumera líneas (debug de scripts).
    * `-A`: Muestra caracteres invisibles (saltos de línea/tabs).
    * `-s`: Comprime líneas en blanco consecutivas.

---

## 📦 3. Compresión y Empaquetado (TAR)
Sirve para juntar archivos. El peso sumado es igual al total a menos que se use compresión.

* **Acciones:** `-c` (Crear), `-t` (Listar), `-x` (Extraer).
* **Modificadores:**
    * `-z`: Gzip (`.tar.gz`).
    * `-j`: Bzip2 (`.tar.bz2`). Nota: Comprime más pero usa más recursos.
    * `-v`: Verbose (ver proceso).
    * `-f`: **Archivo** (Indica que el siguiente argumento es el nombre, poner al final).
    * `-C`: Cambia a un directorio específico antes de operar.
* **Uso óptimo:** `tar czf archivo.tar.gz [directorio]`.

---

## 🔒 4. Redes y Conexiones Seguras

### 📡 SSH & SCP
* **SSH:** Conexión segura (Puerto 22 por defecto). `ssh usuario@host`.
    * `-p`: Especificar puerto.
    * `-v / -vv / -vvv`: Detalles de conexión y llaves.
    * `-i`: Llave de identidad (Key file). Requiere permisos restrictivos.
* **SCP:** Copia de archivos vía SSH. `scp [args] /origen /destino`.
    * `-P`: Puerto (Mayúscula).
    * `-r`: Copiar carpetas enteras.
    * **División:** El `:` separa la máquina de la ruta.

### 🛠️ Netcat (NC) & Nmap
* **Netcat:** Transferencia rápida pero insegura (sin cifrado).
    * **Servidor (Escuchar):** `nc -l -p [puerto]`.
    * **Cliente (Conectar):** `nc [host] [port]`.
    * `-z`: Verifica puerto abierto.
    * `-u`: Usa UDP en lugar de TCP.
* **Nmap:** Analizador de puertos (1000 puertos comunes por defecto).
    * `-p`: Analizar puerto específico.
    * `-sV`: Detecta programa y versión que corre en el puerto.
    * `-A`: Detecta OS y lanza scripts de diagnóstico.

---

## 🔑 5. Permisos y Privilegios (Security Layer)

### 🔹 umask (Definición de restricciones)
Define qué permisos **NO** se otorgan al crear. 
* **Valores:** Read (4), Write (2), Execute (1). Máximo octal: 7.
* **Cálculo (Ejemplo para `rwxr-w--x`):**
    * User: `7 - (4+2+1) = 0`
    * Group: `7 - (4+1) = 2`
    * Others: `7 - 1 = 6`
    * Resultado: `umask 026`.

### 🔹 chmod (Edición de permisos)
Edita permisos sumando valores. Máximo: 777.
* **Ejemplo 751:** Admin (rwx), Grupo (r-x), Otros (--x).
* **Atajos:** `chmod +x` (ejecución), `chmod u-w` (quita escritura al usuario para evitar borrado accidental).

### 🔹 Flags Especiales
* **SETUID (4):** El archivo se ejecuta con privilegios del owner (aparece como `s` en `rws`).
* **SETGID (2):** El archivo se ejecuta con privilegios del grupo (`rwxr-s---`).

---

## ⚙️ 6. Automatización y Control de Trabajos

### 🕒 Crontab (Cron)
Ejecuta scripts en intervalos. Estructura de 5 asteriscos: `* * * * * [Comando]`.
![[Pasted image 20260405134223.png]]
* `*/15 * * * *`: Cada 15 min.
* `0 9-15 * * *`: Cada hora de 9:00 a 15:00.
* **Rutas:** `/etc/crontab` (principal), `/var/spool/cron/crontabs/` (usuario).

### 🖥️ Control de Procesos y Tmux
* **Controles:**
    * `&`: Ejecuta en fondo.
    * `CTRL + Z`: Pausar proceso.
    * `jobs`: Lista procesos en background.
    * `bg`: Reanuda en fondo.
    * `fg`: Trae al frente.
    * `kill %n`: Mata el job número `n`.
* **Tmux (Multiplexor):** Control con `CTRL + B`.
    * `%`: Divide vertical.
    * `"`: Divide horizontal.
    * Flechas: Salta entre consolas.
    * `CTRL + B + Flechas`: Redimensionar.

---

## 🧩 7. Análisis Forense y Criptografía

* **xxd (Hexadecimal):**
    * `-c [n]`: Define bytes por línea.
    * `-l [n]`: Muestra solo los primeros `n` bytes (ver encabezado).
    * `-p`: Solo código hexadecimal plano.
    * `-r -p`: Revierte hexadecimal a lenguaje plano/binario.
* **base64:** Codifica y decodifica (`-d`). ![[Pasted image 20260327201519.png]] ![[Pasted image 20260327201623.png]]
* **Hash:** Huella digital matemática (MD5, SHA). Inevitablemente única.
    * **MD5:** Siempre 32 caracteres. ![[Pasted image 20260405141429.png]]
    * **Uso:** Comparar integridad de archivos o ocultar rutas.
* **diff:** Compara líneas entre archivos.
    * `<`: Primera línea.
    * `---`: Intermedio.
    * `>`: Línea diferente.
    * Filtro rápido: `diff f1 f2 | grep ">"`.

---