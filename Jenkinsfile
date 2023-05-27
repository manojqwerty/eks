pipeline {
  agent any
  stages {
    stage('Install Maven') {
            steps {
                // Install Maven 3.9.2
                tool name: 'Maven 3.9.2', type: 'maven'
            }
        }
      stage('Build') {
       steps {
       bat 'mvn clean & mvn package'
       }
      }
    
  }   
}
