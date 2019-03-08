# Comprobación de la instalación de Hadoop

La verificación de la correcta instalación de Hadoop se ha realizado mediante el tutorial [Installing CHD5 with MRv1 on a Single Linux Node in Pseudo-distributed mode](https://www.cloudera.com/documentation/cdh/5-1-x/CDH5-Quick-Start/cdh5qs_mrv1_pseudo.html), concretamente en el apartado **Running an example application with MRv1**.

En este ejemplo, el primer paso a realizar es el de crear un directorio para el usuario quien ejecutará las tareas del ejemplo. Sin embargo, este paso ya lo ejecuta Ansible en el *playbook*. Por lo tanto, tras haber ejecutado ```$ vagrant up```, procedemos a ejecutar ```$ vagrant ssh``` para conectarnos con la respectiva máquina virtual.

A continuación, creamos un directorio en HDFS llamado *input* y copiamos varios archivos xml en esta carpeta ejecutando los siguientes comandos:
```
$ hadoop fs -mkdir input
$ hadoop fs -put /etc/hadoop/conf/*.xml input
```

Tras esto, y con objeto de comprobar el estado de la carpeta, se ejecuta ```$ hadoop fs -ls input``` para comprobar que 3 archivos se encuentran en la misma.

Más tarde, es necesario aplicar el comando *grep* a los archivos de la carpeta *input* mediante la expresión regular ```dfs[a-z.]+```. Esto lo que hace es ejecutar dos tareas (*map/reduce*) en secuencia. La primera cuenta cuántas veces la expresión regular ha ocurrido, mientras que la segunda ordena las ocurrencias por su frecuencia y las almacena en un fichero en la carpeta *output*. El comando que se utiliza para realizar esto es el siguiente:
```
$ /usr/bin/hadoop jar /usr/lib/hadoop-0.20-mapreduce/hadoop-examples.jar grep input output 'dfs[a-z.]+'
```
Finalmente, para leer el resultado de cualquier archivo de la carpeta *output* se debe ejecutar el siguiente comando:
```
$ hadoop fs -cat output/[file] | head
```

Es importante recalcar que *file* se puede conocer ejecutando ```hadoop fs -ls output```.

* Miembros:
  * Carlos Córdoba Ruiz
  * Cristian Gómez Portes
