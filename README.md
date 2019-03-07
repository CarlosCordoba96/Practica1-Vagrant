# Comprobación de la instalación de Hadoop

La verificación de la correcta instalación de Hadoop se ha realizado mediante el tutorial [Installing CHD5 with MRv1 on a Single Linux Node in Pseudo-distributed mode](https://www.cloudera.com/documentation/cdh/5-1-x/CDH5-Quick-Start/cdh5qs_mrv1_pseudo.html), concretamente en el apartado **Running an example application with MRv1**.

En este ejemplo, el primer paso a realizar es el de crear un directorio para el usuario quien ejecutará las tareas del ejemplo. Sin embargo, este paso ya lo ejecuta Ansible en el *playbook*. Por lo tanto, tras haber ejecutado ```$ vagrant up```, procedemos a ejecutar ```$ vagrant ssh``` para conectarnos con la respectiva máquina virtual.

A continuación, creamos un directorio en HDFS llamado *input* y copiamos varios archivos xml en esta carpeta:
```
$ hadoop fs -mkdir input
$ hadoop fs -put /etc/hadoop/conf/*.xml input
$ hadoop fs -ls input
```

* Miembros:
  * Carlos Córdoba Ruiz
  * Cristian Gómez Portessudo -u hdfs hadoop fs -mkdir -p /user/joe
