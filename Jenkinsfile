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
                sh 'id'
                sh 'cat /etc/group'
                echo 'Hello Worldo'
            }
        }
    }
}