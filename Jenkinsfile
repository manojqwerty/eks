pipeline {
    agent any
    
    environment {
        VAULT_ADDR = "http://54.242.124.50:8200/"
        VAULT_TOKEN = credentials('vault-cred')
    }
    
    stages {
        stage('Fetch Docker Credentials') {
            steps {
                script {
                    def vaultCredentials = vaultCredentials(credentialsId: 'vault-cred', path: 'secret/dockerhub')
                    
                    withCredentials([[$class: 'UsernamePasswordMultiBinding', credentialsId: vault-cred, usernameVariable: 'DOCKER_USERNAME', passwordVariable: 'DOCKER_PASSWORD']]) {
                        // Use Docker credentials here
                        // For example, you can authenticate with Docker registry or build and push Docker images
                        sh 'docker login -u $DOCKER_USERNAME -p $DOCKER_PASSWORD'
                        // Other Docker-related commands
                    }
                }
            }
        }
        
        // Add more stages as needed
    }
}
