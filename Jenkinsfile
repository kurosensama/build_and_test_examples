pipeline {
    agent any

    stages {
        stage('Build Java') {
            steps {
                agent {
                    docker {
                        image 'alpine:latest'
                    }
                }
                echo 'Hello Worldo'
            }
        }
    }
}