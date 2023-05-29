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
                    // Retrieve Docker credentials from Vault using the vault command-line tool
                    def vaultOutput = sh(script: 'vault kv get -format=json secret/dockerhub', returnStdout: true).trim()
                    def dockerCredentials = readJSON text: vaultOutput
                    
                    def DOCKER_USERNAME = dockerCredentials.data.username
                    def DOCKER_PASSWORD = dockerCredentials.data.password
                    
                    // Use Docker credentials here
                    // For example, you can authenticate with Docker registry or build and push Docker images
                    sh "docker login -u ${DOCKER_USERNAME} -p ${DOCKER_PASSWORD}"
                    // Other Docker-related commands
                }
            }
        }
        
        // Add more stages as needed
    }
}
