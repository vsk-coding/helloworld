pipeline {
    
    
    agent {
        label 'WindowsSlave'
        
    }

    stages {
        stage('clean workspace') {
            steps {
                cleanWs()
            }
        }
    
        stage('execute') {
            steps {
                bat label: '', script:  '''git clone https://github.com/vsk-coding/helloworld.git
                cd hellworld
                python helloworld.py
                cd slavetest
                python slave.py'''
            }
        }
    }
}
