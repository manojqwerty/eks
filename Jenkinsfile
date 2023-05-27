pipeline {
  agent any
  tools {
    maven 'maven-3.6.3'
  }
  stages {
      stage('Build') {
       steps {
       echo 'manoj'
       }
      }
      stage('clean') {
       steps {
       sh 'mvn clean'
       }
      }
    stage('test') {
      steps {
        sh 'mvn test'
      }
  }
    
  }   
}
