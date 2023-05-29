pipeline {
    agent any
    
    stages {
        stage('Read DockerHub credentials from Vault') {
            steps {
                script {
                    withVault([
                        vaultCredentialId: 'vault-cred',
                        vaultUrl: 'http://54.242.124.50:8200/'
                    ]) {
                        def credentials = vault.read('secret/dockerhub')
                        env.DOCKER_USERNAME = credentials.data.username
                        env.DOCKER_PASSWORD = credentials.data.password
                    }
                }
            }
        }
        }
    }
}
