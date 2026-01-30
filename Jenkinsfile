pipeline {
    agent any
    
    tools {
        maven 'maven-3.9.12'
        jdk 'java-21'
    }

    stages {

        stage('Clean and Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('SonarCloud Analysis') {
            steps {
                withSonarQubeEnv('sonarqube-server') {
                    sh '''
                        mvn sonar:sonar \
                        -Dsonar.projectKey=mvn-app-org_maven-project \
                        -Dsonar.projectName=maven-project \
                        -Dsonar.organization=mvn-app-org
                    '''
                }
            }
        }

    }
}