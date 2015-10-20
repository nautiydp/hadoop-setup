# hadoop-setup

Hadoop setup:
1- Download jdk latest version:
Move jdk to       /usr/lib directory
Create a java directory in /usr/ lib/
nautiydp$nautiydp-virtual-machine: /usr/lib$ sudo    mkdir   java

nautiydp$nautiydp-virtual-machine: /usr/lib$ sudo   mv    /home/nautiydp/Downloads/jdk1.8.0_40        /usr/lib/java/

nautiydp$nautiydp-virtual-machine: /usr/lib$ sudo   update-alternatives    --install   “/usr/bin/java”     “java”    “usr/lib/java/jdk1.8.0_40/bin/java”  1

nautiydp$nautiydp-virtual-machine: /usr/lib$ sudo   update-alternatives    --install   “/usr/bin/javac”     “javac”    “usr/lib/java/jdk1.8.0_40/bin/javac”  1

nautiydp$nautiydp-virtual-machine: /usr/lib$ sudo   update-alternatives    --install   “/usr/bin/javaws”     “javaws”    “usr/lib/java/jdk1.8.0_40/bin/javaws”  1


2- Edit bashrc file
nautiydp$nautiydp-virtual-machine:~$ gedit    ~/.bashrc
#JAVA HOME DIRECTORY SET UP
Export   JAVA_HOME=”usr/lib/java/jdk1.8.0_40”
set PATH=”$PATH=$PATH:JAVA_HOME/bin”
export  PATH
nautiydp$nautiydp-virtual-machine:~$ java -version




3-SSH   setup: 
nautiydp$nautiydp-virtual-machine:~$ sudo apt-get   install    ssh
if there is some error while installing ssh then run this-  (sudo   apt-get  update)
nautiydp$nautiydp-virtual-machine:~$ ssh-keygen   -t  rsa  -P “”
nautiydp$nautiydp-virtual-machine:~$ cat  $HOME/.ssh/id_rsa.pub  >>  $HOME/.ssh/authorized_keys

nautiydp$nautiydp-virtual-machine: /usr/lib:$ ssh  localhost

4- install jps
nautiydp$nautiydp-virtual-machine:~$ sudo  apt-get    install    openjdk-8-jdk 
ssh localhost
exit
jps

5-: download hadoop-1.2.1 and keep in BigDataExperiment directory
Set hadoop path in bashrc file.
nautiydp$nautiydp-virtual-machine:~$ gedit    ~/.bashrc
#HADOOP HOME DRIVE SETUP
HADOOP_HOME=”BigDataExperiment/hadoop-1.2.1”
export  PATH=”$PATH:$HADOOP_HOME/bin”
nautiydp$nautiydp-virtual-machine:~$ hadoop version
6-BigDataExperiment->cong->hadoop-env.sh        -    hadoop should know java is installed
export   JAVA_HOME=/usr/lib/java/jdk1.8.0_40





7- Edit these files:
core-site.xml
hdfs-site.xm
mapred-site.xml
create a folder inside BigDataExperiment ->     HDFS_Data
core-site.xml:
<configuration>
      <property>
                  <name>hadoop.tm.dir</name>            
                   <value>/home/nautiydp/BigDataExperiment/HDFS_Data</value>
    </property>

      <property>
                  <name>fs.default.name</name>            
                   <value>hdfs://localhost:9000</value>
    </property>
</configuration>

hdfs-site.xml
<property>
     <name>dfs.replication</name>
     <value>1</value>
</property>





mapred-site.xml
<property>
<name>mapred.job.tracker</name>
<value>localhost:9000</value>
</property>


stop-all.sh
start-all.sh
activate name node by running this command
hadoop    namenode      -format

check  here
localhost : 50070


Process the file from HDFS using MapReduce.
nautiydp$nautiydp-virtual-machine:~$ hadoop    jar   /home/nautiydp/BigDataExperiment/hadoop-1.2.1/hadoop-examples-1.2.1.jar   pi    1  1

check here 
localhost:50030
word count problem
copy the program from google and run in eclipse by passing these parameters.
hdfs://localhost:9000/Sample/word.txt
hdfs://localhost:9000/Sample/sample_output

Test
