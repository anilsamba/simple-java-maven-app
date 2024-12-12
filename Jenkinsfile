pipeline {
    agent any

    stages {
        stage('code fetch from github') {
            steps {
                echo 'Fetching the code'
                git branch: 'branch2', url: 'https://github.com/TechWithKhanam/simple-java-maven-app.git'
                  }
         }
        stage('build code/ trigger Maven ') {
            steps {
                echo 'building the code'
                bat 'mvn clean install'
                  }
         }
        stage('test code/ trigger Maven test ') {
            steps {
                echo 'testing the code - SUREFIRE'
                bat 'mvn test'
                  }
         }
        
        stage('VERIFY DOCKERFILE') {
            steps {
                echo 'Verifying Dockerfile presence'
                bat 'dir'
            }
        }
        
        stage('docker image build by jenkins') {
            steps {
                echo 'building docker image'
                bat 'docker build -t myapp1:latest .'
            }
        }
        
        
        stage('deploy code by jenkins') {
            steps {
                echo 'deploying code in docker'
                bat 'docker run -d -p 9090:8080 --name myapp_container1 myapp1:latest'
            }
        }
    }
}
