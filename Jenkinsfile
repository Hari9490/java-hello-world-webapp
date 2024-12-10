pipeline {
    agent any


    stages {
        stage('Checkout') {
            steps {
                // Checkout the code from your Git repository
                git branch: 'master', credentialsId: 'github-cred', url: 'git@github.com:Hari9490/java-hello-world-webapp.git'
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
       
        stage ('Deploy') {
               steps {
                withCredentials([sshUserPrivateKey(credentialsId: 'deploy-server', keyFileVariable: 'keyFile')]) {
                    script {
                          sh 'scp -o StrictHostKeyChecking=no -i ${keyFile} -r /var/lib/jenkins/workspace/hello-world/target/java-hello-world.war azureuser@vm1-jenkins:/opt/tomcat/webapps/'
                    }
                }
                   
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
