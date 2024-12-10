pipeline {
    agent any


    stages {
        stage('Checkout') {
            steps {
                // Checkout the code from your Git repository
                git branch: 'main', credentialsId: ''github-cred'', url: 'git@github.com:Hari9490/interviewinsights-web.git'
            }
        }


        stage('Build') {
            steps {
                // Build the React application
                sh 'mvn --version'
                sh 'mvn -B verify --file pom.xml'
                sh 'mvn compile'
            }
        }
}

    post {
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed.'
        }
    }

   }
