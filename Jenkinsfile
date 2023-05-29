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
                    withVault(configuration: [timeout: 60, vaultCredentialId: 'vault-cred', vaultUrl: 'http://54.242.124.50:8200'], vaultSecrets: [[path: 'secret/dockerhub', secretValues: [[vaultKey: 'username'], [vaultKey: 'password']]]]) {
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
                    sh 'docker tag manu manojreddy12/demo:v1,0'
                }
            }
        }
       stage('docker push') {
            steps {
                script {
                    sh 'docker push manojreddy12/demo:v1,0'
                }
            }
        } 
    }
}
