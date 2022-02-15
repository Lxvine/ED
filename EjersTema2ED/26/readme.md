## 26. CMake. Automatiza el proceso de compilación de ejecutable y bibliotecas, su enlazado y la generación del archivo ejecutable para código fuente en C++. Crea un buildfile con CMake.
A continuación se indica el proceso a seguir para construir o generar el proyecto. 

0. En tu equipo, entra en la carpeta donde guardas tus proyectos.

```bash
cd
mkdir Proyectos  
cd Proyectos
```

1. Descarga el código fuente.

```bash
git  clone  https://github.com/jamj2000/DAW1-ED-Bibliotecas.git
```

2. Entra en el directorio DAW1-ED-Bibliotecas/cpp

```bash
cd  DAW1-ED-Bibliotecas/cpp
```

3. Crea un directorio de construcción y entra en él.

```bash
mkdir  build  &&  cd  build
```

En este directorio se generará el archivo _Makefile_ y el ejecutable y bibliotecas.


4. Para generar el archivo _Makefile_ ejecuta:

```bash
cmake  ..
```

El `..` indica el directorio padre. Es el directorio donde `cmake` debe leer el archivo de configuración `CMakeLists.txt`.

Por defecto, en Linux, para `cmake` el directorio donde se instalará el ejecutable y las bibliotecas se almacena en la variable `CMAKE_INSTALL_PREFIX` cuyo valor es `/usr/local`. Podemos cambiar este valor por otro. Por ejemplo para indicar que el directorio donde se instalará el ejecutable y las bibliotecas sea `/usr`, ejecutamos: 

```bash
cmake  ..  -DCMAKE_INSTALL_PREFIX=/usr
```

5. Comprobamos que se ha generado un archivo __`Makefile`__.

```bash
ls 
cat Makefile
```

6. Ahora podemos realizar el proceso de construcción con el comando `make`:

```bash
make
```

7. Si deseamos realizar la instalación de los archivos generados, hacemos:

```bash
sudo  make  install
```
