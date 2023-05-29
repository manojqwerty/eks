stage('Retrieve Docker Credentials from Vault') {
  steps {
    script {
      def vaultSecret = vault(
        path: 'secret/dockerhub',  // Path to the Docker credentials in the Vault
        engineVersion: 1
      )

      withCredentials([
        usernamePassword(
          credentialsId: vault-cred.data.usernameKey,  // The key for the Docker username in the Vault secret
          passwordVariable: 'DOCKER_PASSWORD',  // Environment variable to store the Docker password
          usernameVariable: 'DOCKER_USERNAME'  // Environment variable to store the Docker username
        )
      ]) {
        // Your Docker-related steps here, where you can use the DOCKER_USERNAME and DOCKER_PASSWORD environment variables
      }
    }
  }
}
