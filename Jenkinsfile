pipeline {
    
    
    agent any

    stages {
        stage('clean workspace') {
            steps {
                cleanWs()
            }
        }
        stage('Code Quality Check via SonarQube') {
            steps {
                script {
                    def scannerHome = tool 'sonar';
                    withSonarQubeEnv("sonar") {
                            sh "sonar-scanner \
                            -Dsonar.projectKey=sample-test \
                            -Dsonar.sources=. \
                            -Dsonar.host.url=https://54163171a8d9.ngrok.io \
                            -Dsonar.login=451c541329a7f6c416fa593084b7d475cce35cfe
                    }
                }
            }
        }
    
        stage('execute') {
            steps {
                bat label: '', script:  '''git clone https://github.com/vsk-coding/helloworld.git
                cd helloworld
                python helloworld.py
                cd slavetest
                python slave.py'''
            }
        }
    }
}
