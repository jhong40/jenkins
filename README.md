# jenkins
- Install

Slave Node:
```
sudo apt update; sudo apt install -y openjdk-8-jdk
sudo useradd -m -s /bin/bash jenkins
sudo passwd jenkins
```

Master:
```
sudo apt update; sudo apt install openjdk-8-jdk
java -version
wget -q -O - https://pkg.jenkins.io/debian-stable/jenkins.io.key | sudo apt-key add -
sudo sh -c 'echo deb http://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'
sudo apt update; sudo apt install jenkins
sudo systemctl start jenkins

# create pub key for slave
sudo su - jenkins
ssh-keygen -t rsa -b 2048
ssh-copy-id jenkins@172.16.150.12  #add pub key to authorized_keys on the slave

```
node {
  echo "Hello World"
}
```
- 1 stage
```
pipeline {
 agent any
 stages {
     stage("Stage1") {
         steps {
             echo "Hello World"
         }
     }
 }
}

```
- parm
```
pipeline {
 agent any
 parameters {
   string(name: 'Greeting', defaultValue: 'Hello', description: "How should I greet the world?")
 }
 stages {
     stage("Example") {
         steps {
             echo "${params.Greeting} World"
         }
     }
 }
}

```
- 2 stages
```
pipeline {
 agent any
 stages {
     stage("Build") {
         steps {
            sh 'echo "Build"'
         }
     }
     stage("BuildMore") {
        steps {
         sh 'echo "Buildmore"'
        }
     }
 }
}
```
