pipeline {
    agent any
    
    stages {
        stage('Fetch') {
            steps {
                // Clean workspace before fetching
                cleanWs()
                
                // Fetch the GitHub repository
                git branch: 'master', credentialsId: 'github', url: 'https://github.com/manojqwerty/eks'
            }
        }
        
        // Add more stages as needed for your build process
        
        stage('Build') {
            steps {
                // Add build steps here
                sh 'echo "Building..."'
            }
        }
        
        stage('Test') {
            steps {
                // Add test steps here
                sh 'echo "Testing..."'
            }
        }
        
        stage('Deploy') {
            steps {
                // Add deployment steps here
                sh 'echo "Deploying..."'
            }
        }
    }
    
    post {
        success {
            // Add success post-build actions here
            echo 'Build succeeded!'
        }
        
        failure {
            // Add failure post-build actions here
            echo 'Build failed!'
        }
    }
}
