pipeline {
    agent any

    stages {
        agent{
            docker{
                image alpine:latest
            }
        }
        stage('Build Java') {
            steps {
                echo 'Hello Worldo'
            }
        }
    }
}
