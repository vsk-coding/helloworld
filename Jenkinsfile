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
        stage('Code Quality Check via SonarQube')
        {
            steps
            {
                script
                {
                    withSonarQubeEnv("sonar-scanner")
                    {
                            sh ''' /opt/sonar/bin/sonar-scanner \
                            -Dsonar.projectKey=sample-test \
                            -Dsonar.sources=. \
                            -Dsonar.host.url=https://192.168.101.12:9000 \
                            -Dsonar.login=e48e73ab578155675f96f269ccedaeb39fa899cb '''
                    }
                }
            }
        }
    }
}
