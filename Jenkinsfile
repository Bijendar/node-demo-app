
pipeline {
    agent any  // Run on any available Jenkins agent

    stages {

        stage('Checkout Code') {
            steps {
                echo 'Cloning code from GitHub...'
                git url: 'https://github.com/Bijendar/node-demo-app.git', branch: 'main'  // make sure to place the Jenkinsfile in this repo   
                echo 'Code cloned successfully!'
            }
        }

        stage('Build Docker Image') {
            steps {
                echo 'Building Docker image...'
                // Go into the app directory if Dockerfile is inside node-demo-app
                dir('Task 1/node-demo-app') {
                    sh 'docker build -t node-demo-app-image:latest .'
                }
                echo 'Image build complete!'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying application using Docker...'
                // Run the container, bind to port 3000 (or as needed)
                sh 'docker run -d -p 3000:3000 node-demo-app-image:latest'
                echo 'Deployment successful!'
            }
        }
    }
}
