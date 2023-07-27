# Maven Installation
### Install Maven on Jenkins Server
- Go to https://maven.apache.org/download.cgi
- Copy Link address for link next to Binary tar.gz archive
- Enter following commands in terminal:
  ```sh
  cd /opt
  wget https://dlcdn.apache.org/maven/maven-3/3.9.3/binaries/apache-maven-3.9.3-bin.tar.gz
  tar -xvzf apache-maven-3.8.8-bin.tar.gz
  mv apache-maven-3.8.8 maven
  ```
- Next we will add JAVA, M2_HOME and M2 paths in .bash_profile
  ```sh
  vi ~/.bash_profile
  M2_HOME=/opt/maven
  M2=/opt/maven/bin
  JAVA_HOME=/usr/lib/jvm/java-11-openjdk-11.0.19.0.7-1.amzn2.0.1.x86_64
  # get java path from cd /usr/lib/jvm
  PATH=$PATH:$HOME/bin:$JAVA_HOME:$M2_HOME:$M2
  ```
### Configure Maven on Jenkins Console
- Manage Jenkins > Plugins > Available Plugins > Maven Integration > Install Without Restart
- Manage Jenkins > Tools > Maven > Unselect Install Automatically > Maven Name "maven-version number" > Maven_Home "is path of maven" i.e. /opt/maven
- Apply > Save
