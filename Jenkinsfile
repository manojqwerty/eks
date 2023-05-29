pipeline {
    agent any
    
    
    stages {
        stage('Read DockerHub credentials from Vault') {
            steps {
                script {
                    withVault([VaultConfiguration: 'vault-cred']) {
                        def credentials = vault('secret/dockerhub')
                        env.DOCKER_USERNAME = credentials.username
                        env.DOCKER_PASSWORD = credentials.password
                    }
                }
            }
        
        }
    }
}
