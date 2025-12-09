# 🧰 CommonUtils – Utilidades compartidas para proyectos Qt/C++

CommonUtils es una pequeña librería surgida de la necesidad de centralizar funcionalidades que estaba repitiendo en varios proyectos Qt.  
Aunque nació más como un experimento para aprender sobre la creación de librerías y la modularización del código.

---

## ✨ Funcionalidades incluidas

### 📁 FileUtils
Conjunto de utilidades para interacción básica con archivos y directorios:

- `appendText(path, data)` — agrega texto a un archivo.
- `copyAndOverwrite(source, target)` — copia un archivo reemplazándolo si existe.
- `createFolder(dir)` — crea un directorio, incluyendo subdirectorios.
- `replaceOrCreateFile(path, data)` — sobrescribe o crea un archivo.
- `readFile(path)` — lee un archivo y retorna su contenido.
- `searchFile(baseDir, fileInfo, ignoreList)` — búsqueda recursiva de un archivo.
- `copyFilesFromDir(sourceDir, targetDir)` — copia todos los archivos desde un directorio a otro, respetando estructura y evitando duplicados.

### 🧩 JsonUtils
Pequeña utilidad para validación de JSON:

- `isValid(data)` — verifica si un `QByteArray` contiene un JSON bien formado.

### 🗜 ZipUtils
Wrapper alrededor de PowerShell para comprimir y descomprimir ZIPs:

- `compressFiles(sourceDir, outputZipPath)` — comprime archivos usando PowerShell.
- `decompressZipFile(zipFilePath, destinationDir)` — descomprime un ZIP.
- Señales:
  - `compressFinished(exitCode, errorMessage)`
  - `decompressFinished(exitCode, errorMessage)`

> La librería ejecuta los comandos usando `QProcess` y notifica el resultado mediante señales Qt.

---

## 🎯 Objetivo de la librería

Centralizar utilidades repetidas entre proyectos:

- Sin dependencias externas.
- Código simple y reutilizable.
- Evitar duplicación de funciones comunes como lectura de archivos, copia recursiva, validación JSON, etc.
- 
---

## 🧱 Consideraciones técnicas

- Los comandos ZIP dependen de **PowerShell**, por lo que esta funcionalidad es válida para entornos Windows.
- La clase ZipUtils hereda de `QObject` para integrarse correctamente con señales/slots y con el sistema de padres e hijos de Qt.
- No utiliza dependencias adicionales más allá de QtCore y QtProcess.    

---
