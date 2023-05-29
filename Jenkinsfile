pipeline {
    agent any
    
    
    stages {
        stage('Read DockerHub credentials from Vault') {
            steps {
                script {
                    withVault(configuration: [timeout: 60, vaultCredentialId: 'vault-cred', vaultUrl: 'http://54.242.124.50:8200'], vaultSecrets: [[path: 'secret/dockerhub', secretValues: [[vaultKey: 'username'], [vaultKey: 'password']]]]) {
              sh 'docker login -u $username -p $password'
}
                }
            }
        
        }
    }
}
