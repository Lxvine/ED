## 21. Bibliotecas. Busca información y explica las ventajas y desventajas de usar bibliotecas dinámicas.

Las ventajas de las bibliotecas dinámicas son las siguientes: 

- Ahorran más memoria y reducen el intercambio de páginas.

- El archivo so es independiente del archivo .exe, siempre que la interfaz de salida permanezca igual (es decir, el nombre, los parámetros, el tipo de valor de retorno y la convención de llamada no cambien), reemplazar el archivo so no causará al archivo .exe cualquier impacto, mejorando así la capacidad de mantenimiento y la escalabilidad.

- Los programas escritos en diferentes lenguajes de programación pueden llamar a la biblioteca para que funcionen siempre que sigan la convención de llamada de función.

- Es adecuado para el desarrollo de software a gran escala, lo que hace que el proceso de desarrollo sea independiente y menos acoplado, lo que es conveniente para el desarrollo y las pruebas entre diferentes desarrolladores y organizaciones de desarrollo.

Las desventajas de las bibliotecas dinámicas son las siguientes:

- La velocidad es menor, a diferencia de las bibliotecas estáticas, estas necesitan ir a buscar cada una de las funciones requeridas cada vez que se hace un llamamiento.

- Si se quiere ejecutar el archivo es necesario tener instaladas las bibliotecas en el sistema que lo va a ejecutar.

- En caso de modificar las bibliotecas de alguna manera habría que modificar el código fuente del ejecutable para que este funcionara con normalidad.

