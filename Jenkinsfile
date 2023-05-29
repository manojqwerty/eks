pipeline {
    agent any

    stages {
        stage('Docker Login') {
            steps {
                script {
                    def vaultUrl = "http://54.242.124.50:8200/" // Replace with your Vault URL
                    def secretPath = "secret/dockerhub" // Replace with your secret path in Vault
                    def vaultToken= "mysecret"
                    // Retrieve Docker Hub credentials from Vault
                    def credentials = sh(
                        returnStdout: true,
                        script: "curl -s -H 'X-Vault-Token: ${vaultToken}' ${vaultUrl}/v1/${secretPath}"
                    ).trim()
                    
                    def dockerHubUsername = credentials.data.username
                    def dockerHubPassword = credentials.data.password

                    
                }
            }
        }
        
    }
}
