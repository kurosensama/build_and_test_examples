pipeline {
    agent any

    stages {
        stage('Build') {
            parallel {
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
                    unzip ant.zip -o
                    export PATH=$PATH:$(pwd)/apache-ant-1.10.14/bin
                    java --version
                    ant -version
                    ant jar
                    java -classpath build/lib/math.jar math.Fibonacci 30
                    ant test
                    cat build/test/xml/TESTS-TestSuites.xml
                    ant test-report
                    cat build/test/html/index.html
                '''
            }
        }
        stage('Build python') {
            agent {
                docker {
                    image 'alpine:latest'
                    args '--user root'
                    reuseNode true
                }
            }
            steps {
                sh '''
                    cd python
                    apk add python3 py3-pytest
                    python --version
                    pytest --version
                    python maths/fibonacci.py 30
                    pytest --junit-xml=report.xml
                    cat report.xml
                '''
            }
        }
            }
        }
    }
    post { 
        failure { 
            cleanWs()
        }
    }
}