## 18. Bibliotecas. Crea una biblioteca dinámica en C que proporcione las funciones para restar, sumar, multiplicar y dividir 2 números enteros. Crea un programa que haga uso de ella y comprueba que se ejecuta correctamente.

## Archivo de cabecera:

	int suma (int sumando1, int sumando2);

	int resta  (int minuendo, int sustraendo);

	int multiplicacion (int  numero1, int numero2);

	float division (int dividendo, int divisor);

## Archivo de código:

	int suma (int sumando1, int sumando2) {
		return (sumando1+sumando2);
	}


	int resta  (int minuendo, int sustraendo) {
		return (minuendo-sustraendo);
	}


	int multiplicacion (int  numero1, int numero2) {
		return (numero1*numero2);
	}


	float division (int dividendo, int divisor) {
		return (dividendo/(float)divisor);
	}

## Para crear una biblioteca dinámica seguimos los siguientes pasos:

1 Compilamos a código objeto dinámico con:

	gcc  -c  -fPIC  aritmetica.c

Se genera un archivo aritmetica.c con código objeto dinámico.

2 Empaquetamos en biblioteca dinámica libaritmetica.so con: 

	gcc  -shared  -fPIC  -o  libaritmetica.so  aritmetica.o

3 Instalamos biblioteca en el sistema.

Para instalar dicha biblioteca en el sistema debemos copiar libaritmetica.so a algún directorio del sistema donde se alojan las bibliotecas:

	cp  libaritmetica.so  /lib

## Para utilizar biblioteca dinámica como plugin:


Archivo Plug.c:


	#include <dlfcn.h>
	#include <stdio.h>

	#define NUM1	5
	#define NUM2	2


	int main (){
		void *h = dlopen("./libaritmetica.so", RTLD_LAZY);

		printf ("Dados los números %d y %d\n", NUM1, NUM2);

		int (*test)() = dlsym (h, "suma");
		printf ("La suma es %d\n", (*test)(NUM1, NUM2));

		test = dlsym (h, "resta");
		printf ("La resta es %d\n", (*test)(NUM1, NUM2));

		test = dlsym (h, "multiplicacion");
		printf ("La multiplicación es %d\n", (*test)(NUM1, NUM2));

		float (*test2)() = dlsym (h, "division");
		printf ("La división es %f\n", (*test2)(NUM1, NUM2));
		return 0;
	}

1 Compilamos y enlazamos, generando un ejecutable plug:

	gcc  -o  plug  plug.c  -ldl

2 Ejecutamos programa plug:

	./plug

## Crear ejecutable con enlace dinámico:

Creamos archivo main.c 

	#include <stdio.h>
	#include "aritmetica.h"

	#define NUM1	5
	#define NUM2	2


	int main (){
		printf ("Dados los números %d y %d\n", NUM1, NUM2);
		printf ("La suma es %d\n", suma (NUM1, NUM2));
		printf ("La resta es %d\n", resta (NUM1, NUM2));
		printf ("La multiplicación es %d\n", multiplicacion (NUM1, NUM2));
		printf ("La división es %f\n", division (NUM1, NUM2));
	return 0;
	}

1 Compilamos y enlazamos, generando un ejecutable main y enlace dinámico a libaritmetica.so

	gcc  -o  main  main.c  libaritmetica.so 

2 Comprobamos vínculos dinámicos:

	ldd  main


