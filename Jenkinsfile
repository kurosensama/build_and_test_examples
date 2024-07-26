pipeline {
    agent any

    stages {
        stage('Build Java') {
            agent {
                docker {
                    image 'alpine:latest'
                    args '--user root'
                    reuseNode true
                }
            }
            steps {
                sh '''
                    cd java
                    apk add curl
                    apk add openjdk11
                    curl -o ant.zip "https://dlcdn.apache.org//ant/binaries/apache-ant-1.10.14-bin.zip"
                    unzip ant.zip
                    export PATH=$PATH:$(pwd)/apache-ant-1.10.14/bin
                    java --version
                    ant --version
                '''
            }
        }
    }
    post { 
        always { 
            cleanWs()
        }
    }
    
}