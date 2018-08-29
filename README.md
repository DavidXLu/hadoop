# hadoop
Setup  hadoop

Hadoop on Ubuntu
# install jdk
sudo apt-get install update
sudo apt-get update
sudo apt-get install default-jdk
java -versionS
# switch jdk
sudo update-alternatives --config java

# add group and user
sudo addgroup hadoop
sudo adduser --ingroup hadoop hadoop
sudo adduser hadoop sudo
# install ssh
sudo apt-get install openssh-server
su - hardoop
ssh-keygen -t rsa -P ""
cat $HOME/ .ssh/id-rsa.pub >> $HOME/.ssh/authorized_keys
ssh localhost
exit

# download hadoop
sudo tar xvzf [your_hadoop.gz]
sudo mv [your_hadoop_folder] /usr/local/hadoop
sudo chown hadoop /usr/local/hadoop

# config .bashrc
export JAVA_HOME=/usr/lib/jvm/java-8-openjdk-amd64
export HADOOP_HOME=/usr/local/hadoop
export PATH=$PATH:$HADOOP_HOME/bin
export PATH=$PATH:$HADOOP_HOME/sbin
export HADOOP_MAPRED_HOME=$HADOOP_HOME
export HADOOP_COMMON_HOME=$HADOOP_HOME
export HADOOP_HDFS_HOME=$HADOOP_HOME
export YARN_HOME=$HADOOP_HOME
export HADOOP_COMMON_LIB_NATIVE_DIR=$HADOOP_HOME/lib/native
export HADOOP_OPTS="-Djava.library.path=$HADOOP_HOME/lib"

# hadoop-env.sh
export JAVA_HOME=/usr/lib/jvm/java-8-openjdk-amd64

# core-site.xml
<property>
<name>fs.default.name</name>
<value>hdfs://localhost:9000</value>
</property>

# hdfs-site.xml
<property>
<name>dfs.replication</name>
<value>1</value>
</property>
<property>
<name>dfs.namenode.name.dir</name>
<value>file:/usr/local/hadoop_tmp/hdfs/namenode</value>
</property>
<property>
<name>dfs.datanode.data.dir</name>
<value>file:/usr/local/hadoop_tmp/hdfs/datanode</value>
</property>

# yarn-site.xml

<property>
<name>yarn.nodemanager.aux-services</name>
<value>mapreduce_shuffle</value>
</property>
<property>
<name>yarn.nodemanager.aux-services.mapreduce.shuffle.class</name>
<value>org.apache.hadoop.mapred.ShuffleHandler</value>
</property>

# mapred-site.xml

<property>
<name>mapreduce.framework.name</name>
<value>yarn</value>
</property>

# run hadoop
hdfs namenode -format
start-dfs.sh
start-yarn.sh
http://localhost:9870

# run job
hadoop jar [your_jar] [class_name] [attributes...]

# install IntelliJ
sudo apt-add-repository ppa:mmk2410/intellij-idea
sudo apt-get update
sudo apt-get install intellij-idea-community
