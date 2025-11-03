pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: 'main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/priaansh11/Test1repo.git']]])
            }
        }
        stage('Build') {
            steps {
                git branch: 'main', url: 'https://github.com/priaansh11/Test1repo.git'
                bat 'python app.py'
            }
        }
        stage('Test') {
            steps {
                echo 'TESTING'
            }
        }
         stage('Docker Deploy') {
            steps {
                echo 'Building Docker image...'
                // Build Docker image (tag as 'myapp:latest')
                bat 'docker build -t myapp:latest .'

                echo 'Running Docker container...'
                // Run Docker container on port 5000
                bat 'docker run -d --name myapp_container11 myapp:latest'

                echo 'Docker deployment completed!'
            }
        }
    }
}
