pipeline {
    agent any

    stages {
        stage('SCM') {
            steps {
                echo 'Fetching the code'
                git branch: 'branch1', changelog: false, poll: false, url: 'https://github.com/TechWithKhanam/simple-java-maven-app.git'
            }
        }
        stage('BUILD') {
            steps {
                echo 'Building the project'
                bat 'mvn clean install'
            }
        }
        stage('TEST') {
            steps {
                echo 'Testing the project'
                bat 'mvn test'
            }
        }
        stage('VERIFY DOCKERFILE') {
            steps {
                echo 'Verifying Dockerfile presence'
                bat 'dir'
            }
        }
        stage('DEPLOY') {
            steps {
                echo 'Deploying the project in Docker container'
                script {
                    // Check if Docker is running and available
                    bat 'docker --version'
                    
                    // Build the Docker image
                    bat 'docker build -t myapp1:latest .'
                    
                    // Run the Docker container
                    bat 'docker run -d -p 9090:8080 --name myapp_container myapp1:latest'
                }
            }
        }
    }
}
