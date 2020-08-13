pipeline {
    agent any
    stages
    {
        stage('clean workspace')
        {
            steps
            {
                cleanWs()
            }
        }
        stage("Code Checkout from Github") {
            steps {
                git branch: 'test',
                url: 'https://github.com/vsk-coding/helloworld.git'
            }
        }      
        stage('Code Quality Check via SonarQube')
        {
            steps
            {
                script
                {
                    withSonarQubeEnv("sonar-scanner")
                    {
                            sh ''' /opt/sonar-scanner/bin/sonar-scanner \
                            -Dsonar.projectKey=sample-test-test \
                            -Dsonar.sources=. \
                            -Dsonar.host.url=http://172.17.0.3:9000/ \
                            -Dsonar.login=e48e73ab578155675f96f269ccedaeb39fa899cb '''
                    }
                }
            }
        }
    }
}
