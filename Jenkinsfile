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
                    sh 'vault kv get -format=json secret/dockerhub'
                    
                
                }
            }
        }
    }
}       
