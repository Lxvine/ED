## 23. Build. Automatiza el proceso de compilación de ejecutable y biblioteca, su enlazado y la generación del archivo .jar para código fuente en Java con Ant. Haz uso de un buildfile.

## build.xml

<?xml version="1.0" encoding="UTF-8"?>
<project name="programa" default="jar" basedir=".">
  <description>Programa que usa biblioteca aritmetica.</description>
    <!-- Ejemplo de archivo de construcción (buildfile)
         Para crear este archivo se ha consultado:
         https://ant.apache.org/manual/tutorial-HelloWorldWithAnt.html
         (cc0) jamj2000
    -->
    <property name="src.dir"     value="."/>
    <property name="build.dir"   value="build"/>
    <property name="classes.dir" value="${build.dir}/classes"/>
    <property name="jar.dir"     value="${build.dir}/jar"/>
    <property name="main-class"  value="Main"/>


    <!-- Creamos directorios para el resultado de la compilación --> 
    <target name="init">
      <mkdir dir="${classes.dir}"/>
      <mkdir dir="${jar.dir}"/>
    </target>


    <!-- Indicamos directorio donde se hallan las clases --> 
    <path id="compile.classpath">
        <fileset dir="aritmetica" />
    </path>


    <!-- Compilamos --> 
    <target name="compile" depends="init" >
      <javac srcdir="${src.dir}" destdir="${classes.dir}" includeantruntime="false" debug="true" >
        <classpath refid="compile.classpath"/>
      </javac>
    </target>


    <!-- Creamos archivo .jar --> 
    <target name="jar" depends="compile">
      <jar destfile="${jar.dir}/${ant.project.name}.jar" basedir="${classes.dir}">
        <manifest>
          <attribute name="Main-Class" value="${main-class}"/>
        </manifest>
      </jar>
    </target>


    <!-- Ejecutamos --> 
    <target name="run" depends="jar">
      <java jar="${jar.dir}/${ant.project.name}.jar" fork="true"/>
    </target>


    <!-- Borramos archivos generados --> 
    <target name="clean">
      <delete dir="build" />
    </target>


    <!-- Mostramos ayuda --> 
    <target name="help">      
      <echo level="info">
        Objetivos válidos para ant:

          jar (el objetivo por defecto si no se indica nada)
          compile
          run
          clean
          help
      </echo>
    </target>

</project>


  ant

  
