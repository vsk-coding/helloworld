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
                    withSonarQubeEnv("sonar")
                    {
                            sh ''' /opt/sonarqube/bin/sonar-scanner \
                            -Dsonar.projectKey=sample-test \
                            -Dsonar.sources=. \
                            -Dsonar.host.url=https://172.17.0.3:9000 \
                            -Dsonar.login=e48e73ab578155675f96f269ccedaeb39fa899cb '''
                    }
                }
            }
        }
    }
}
