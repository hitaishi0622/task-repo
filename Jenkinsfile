pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/hitaishi0622/task-repo.git'
            }
        }

        stage('Compile Java Code') {
            steps {
                script {
                    sh 'javac Test.java' // Compile the Java file
                }
            }
        }

        stage('Run Java Code') {
            steps {
                script {
                    sh 'java Test' // Run the compiled Java class
                }
            }
        }

        stage('Deploy') {
            steps {
                script {
                     echo 'Deploying the application...'
                    // Example: Copy files to a remote server using SCP
                    sh 'scp Test.class user@remote-server:/path/to/destination/'
                    
                    // Example: Run a deployment script on the remote server
                    sh 'ssh user@remote-server "cd /path/to/destination/ && ./deploy.sh"'
                }
                }
            }
        }
    }

    post {
        success {
            echo 'Pipeline succeeded!'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}