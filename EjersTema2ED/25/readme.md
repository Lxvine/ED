## 25. Build. Automatiza el proceso de compilación de ejecutable y biblioteca, su enlazado y la generación del archivo .jar para código fuente en Java con Gradle. Haz uso de un buildfile.

Vamos a crear una aplicación llamada `miapp`. Constará de 2 clases, una principal y otra con la funcionalidad para realizar las cuatro operaciones aritméticas básicas. 

Para ello sigue los siguientes pasos:

0. En tu carpeta de proyectos crea una carpeta llamada miapp y entra en ella: 

```
cd  ~/Proyectos
mkdir  miapp  &&  cd  miapp
```

1. Crea la estructura de carpetas con gradle:

```
gradle  init  --type  java-application
```

2. Veras que se han creado una estructura de directorios y un _buildfile_ llamado __build.gradle__.

3. Genera el siguiente código fuente:

__Primero, borra las clases que vienen por defecto:__

```
rm  src/main/java/App.java  src/test/java/AppTest.java
```

__Crea 2 clases dentro de la ruta `src/main/java`:__

```
nano  src/main/java/Main.java
```


```java
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
```

```
nano  src/main/java/Aritmetica.java
```


```java
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
```

__Crea 2 clases de test dentro de la ruta `src/test/java`:__

```
nano  src/test/java/MainTest.java
```

```java
import org.junit.Test;
import static org.junit.Assert.*;

public class MainTest {

  @Test
  public void testMain() {
      // Prueba vacía
  }
}
```

```
nano  src/test/java/AritmeticaTest.java
```

```java
import org.junit.Test;
import static org.junit.Assert.*;

public class AritmeticaTest {
    
    @Test 
    public void testSuma() {
        assertEquals("Suma (2,3) = 5", 5, Aritmetica.suma(2,3));
    }

}
```


4. Edita el archivo `build.gradle` para que tenga el siguiente contenido:

```
apply plugin: 'java'
apply plugin: 'application'

repositories {
    jcenter()  
}

dependencies {
    compile 'com.google.guava:guava:23.0' 
    testCompile 'junit:junit:4.12'         
}

jar {
    manifest {
       attributes ('Main-Class': 'Main')
    }
}

mainClassName = 'Main'
```


5. Para compilar hacemos:

```
./gradlew  assemble
```

En la carpeta `build/classes` obtendremos el bytecode correspondiente a cada clase.


Una forma de ejecutar el bytecode es:

```bash
cd build/classes/main  &&  java Main  &&  cd ../../..
```


6. El archivo .jar se ha guardado en la carpeta `build/libs`. Para ejecutar dicho archivo .jar:

```
./gradlew  run
```

Otra forma de ejecutarlo es

```
java  -jar  build/libs/miapp.jar
```

7. Para ejecutar las pruebas unitarias:

```
./gradlew  test
```

Para ver un informe de las pruebas, podemos abrir con el navegador web el archivo `build/reports/tests/test/index.html`:

```
firefox build/reports/tests/test/index.html
```

Si obtenemos algún error, podemos limpiar la construcción con `./gradlew  clean`. Revisaremos el código y volveremos a empezar.

