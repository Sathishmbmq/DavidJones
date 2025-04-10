pipeline {
    agent any

    stages {
        stage('SCM') {
            steps {
                echo 'Fetching the code'
                git changelog: false, poll: false, url: 'https://github.com/Sathishmbmq/DavidJones.git'
            }
        }

        stage('BUILD') {
            steps {
                echo 'Building the project'
               // bat 'mvn clean install'
            }
        }

        stage('TEST') {
            steps {
                echo 'Testing the project'
               // bat 'mvn test'
            }
        }

        stage('VERIFY DOCKERFILE') {
            steps {
                echo 'Verifying Dockerfile presence'
                bat 'dir Dockerfile'
            }
        }

        stage('DEPLOY') {
            steps {
                echo 'Checking Docker version'
                bat 'docker --version'

                echo 'Building Docker image'
                bat 'docker build -t myapp1:latest .'

                echo 'Running Docker container'
                bat 'docker run -d -p 9090:8080 --name myapp_container4 myapp1:latest'
            }
        }
    }
}
