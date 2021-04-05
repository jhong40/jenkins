# jenkins
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
