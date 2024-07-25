pipeline {
    agent any

    stages {
        stage('Build Java') {
            agent {
                docker {
                    image 'alpine:latest'
                }
            }
            steps {
                echo 'Hello Worldo'
            }
        }
    }
}