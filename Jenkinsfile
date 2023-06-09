pipeline {
    agent any
    
    
    
    stages {
        stage('get code from scm') {
            steps {
                script {
                    sh 'git --version'
                }
            }
        }
        stage('mvn build') {
            steps {
                script{
                    sh 'mvn --version'
                }
            }
        }
        stage('Read DockerHub credentials from Vault') {
            steps {
                script {
                    withVault(configuration: [timeout: 60, vaultCredentialId: 'vault-cred', vaultUrl: 'http://184.73.135.200:8200'], vaultSecrets: [[path: 'secret/dockerhub', secretValues: [[vaultKey: 'username'], [vaultKey: 'password']]]]) {
              sh 'docker login -u $username -p $password'
             }
                }
            }
        
        }
        stage('docker build') {
          steps {
            script{
                sh 'docker build -t manu .'
            }
          }
        }
        stage('docker tag') {
            steps {
                script {
                    sh 'docker tag manu manojreddy12/demo:v1.0'
                }
            }
        }
       stage('docker push') {
            steps {
                script {
                    sh 'docker push manojreddy12/demo:v1.0'
                }
            }
        } 
        stage('Running the application') {
            steps {
                script {
                    sh 'docker run -itd --name sample -p 8080:8080 manojreddy12/demo:v1.0'
                }
            }
        }
        stage('Print Container ID') {
            steps {
                // Print the container ID
                script {
                    def containerId = sh(returnStdout: true, script: 'docker ps -aqf "name=sample"').trim()
                    echo "Container ID: ${containerId}"
                }
            }
        }
        stage('remove tomcat user.xml') {
            steps {
                script {
                    sh 'docker exec -t sample ls -l'
                    sh 'rm -rf conf/tomcat-users.xml'
                    sh 'exit'
                    sh 'docker cp tomcat-users.xml sample:/usr/local/tomcat/conf/'
                    sh 'docker restart sample'
                }
            }
        }
    }
}
