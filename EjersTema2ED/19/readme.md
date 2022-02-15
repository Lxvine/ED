	## 19. Bibliotecas, Crea una biblioteca dinámica en Java que proporcione las funciones para sumar, restar, multiplicar y dividir 2 números enteros. Crea un programa que haga uso de ella y comprueba que se ejecute correctamente.

## Crear paquete jar con la biblioteca

1 Creamos clase aritmetica/Aritmetica.java

	package aritmetica;

	public class Aritmetica {

	public static int suma (int sumando1, int sumando2) {
		return (sumando1+sumando2);
	}

	public static int resta  (int minuendo, int sustraendo) {
		return (minuendo-sustraendo);
	}

	public static int multiplicacion (int  numero1, int numero2) {
		return (numero1*numero2);
	}

	public static float division (int dividendo, int divisor) {
	        return (dividendo/(float)divisor);
		}

	}

2 Compilamos:

	javac  aritmetica/Aritmetica.java

Obtenemos un archivo aritmetica/Aritmetica.class con el bytecode.

3 Creamos paquete jar

	jar  cvf  aritmetica.jar  aritmetica/*.class

4 Instalamos biblioteca en el sistema

Para instalar dicha biblioteca en el sistema debemos copiar aritmetica.jar al directorio de sistema donde se alojan las librerias de extensiones.

	mv  aritmetica.jar  /usr/lib/jvm/java-8-openjdk-amd64/jre/lib/ext/aritm.jar

## Crear programa que use la biblioteca.

1 Creamos archivo Main.java

 
	import aritmetica.Aritmetica;

	public class Main {

	private static final int NUM1 = 5;
	private static final int NUM2 = 2;


	public static void main (String[] args) {
		System.out.println ("Dados los números " + NUM1 + " y " + NUM2 );
		System.out.println ("La suma es " + Aritmetica.suma(NUM1, NUM2) );
		System.out.println ("La resta es " + Aritmetica.resta(NUM1, NUM2) );
		System.out.println ("La multiplicación es " + Aritmetica.multiplicacion(NUM1, NUM2) );
		System.out.println ("La división es " + Aritmetica.division(NUM1, NUM2) );
	}

	}

2 Compilamos
	
	javac  Main.java

Obtenemos un archivo Main.class con el bytecode. Al compilar, se enlaza con las bibliotecas necesarias, buscando éstas en el directorio de bibliotecas del sistema.

3 Ejecutamos

	java Main

Al ejecutar, se buscan las bibliotecas necesarias en el directorio de bibliotecas del sistema.


