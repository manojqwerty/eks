pipeline {
    agent any
    
    environment {
        DOCKER_REGISTRY = 'docker.io'
        DOCKER_REGISTRY_CREDENTIALS = 'dockerhub-credentials'
    }
    
    stages {
        stage('Read DockerHub credentials from Vault') {
            steps {
                withVault(credentialsId: 'vault-cred') {
                    script {
                        def credentials = vaultCredential('secret/dockerhub')
                        env.DOCKER_USERNAME = credentials.data.username
                        env.DOCKER_PASSWORD = credentials.data.password
                    }
                }
            }
        }
        
    }
}
