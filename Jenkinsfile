pipeline {
    agent any
    
    stages {
        stage('Docker Login') {
            steps {
                script {
                    // Set up Docker credentials
                    withCredentials([usernamePassword(credentialsId: 'docker-credentials', passwordVariable: 'DOCKER_PASSWORD', usernameVariable: 'DOCKER_USERNAME')]) {
                        
                        // Docker login
                        sh "docker login -u ${DOCKER_USERNAME} -p ${DOCKER_PASSWORD}"
                        
                        // You can also specify the Docker registry URL if necessary
                        // sh "docker login -u ${DOCKER_USERNAME} -p ${DOCKER_PASSWORD}"
                    }
                }
            }
        }
        
        // Add additional stages as needed
        // ...
    }
    
    // Post-build actions, if any
    // ...
}
