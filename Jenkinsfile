pipeline {
    agent any
    environment {
        SONAR_RUNNER_HOME = '/home/jenkins/sonar-scanner'
        PATH = "${SONAR_RUNNER_HOME}/bin:${env.PATH}"
    }
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/rthoma38/my_sonar_project.git'
            }
        }
        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('SonarQube Scanner') {
                    sh 'sonar-scanner -Dsonar.projectKey=sonarqubeproject -Dsonar.sources=. -Dsonar.host.url=http://localhost:9000 -Dsonar.login=$SONARQUBE_TOKEN'
                }
            }
        }
    }
}
