# jenkins
```
node {
  echo "Hello World"
}
```

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
