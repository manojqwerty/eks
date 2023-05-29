pipeline {
    agent any

    stages {
        stage('Retrieve Docker Credentials') {
            steps {
                script {
                    // Install and configure the Vault plugin
                    def vaultPlugin = Jenkins.instance.getPlugin('hashicorp-vault-plugin')
                    if (!vaultPlugin) {
                        error("Vault plugin not installed. Please install the 'HashiCorp Vault Plugin' from the Jenkins Plugin Manager.")
                    }

                    // Read Docker credentials from Vault
                    withVault([vaultCredential: 'my-vault-credential']) {
                        def credentials = vaultRead path: 'secret/dockerhub', format: 'json'
                        def dockerUsername = credentials.data.username
                        def dockerPassword = credentials.data.password

                        // Set Docker credentials in the environment
                        withCredentials([usernamePassword(credentialsId: 'vault-cred', usernameVariable: 'DOCKER_USERNAME', passwordVariable: 'DOCKER_PASSWORD')]) {
                                # Use Docker credentials
                               sh 'docker login -u $DOCKER_USERNAME -p $DOCKER_PASSWORD'
                        }
                    }
                }
            }
        }
    }
}
