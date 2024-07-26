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
                sh '''
                    apk add curl
                    curl "https://download.oracle.com/java/22/latest/jdk-22_linux-x64_bin.deb"
                    dpkg -i *.deb
                    curl "https://dlcdn.apache.org//ant/binaries/apache-ant-1.10.14-bin.zip"
                    unzip *.zip
                    export PATH=$PATH:$pwd/apache*/bin
                    java --version
                    ant --version
                '''
            }
        }
    }
}