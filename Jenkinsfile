pipeline {
    agent any
    
    tools {

        maven 'maven-3.9.12'
        jdk 'java-21'
    }

    stages {
        stage('Clean and Build the Application'){
            steps{
                sh 'mvn clean package'
            }
    }

        stage('Sonarcloud Analysis') {
            steps{
                withSonarQubeEnv('sonarqube-server') {
                    sh 'mvn clean package sonar:sonar -Dsonar.projectKey=mvn-app-org_maven-project -Dsonar.projectName=maven-project -Dsonar.organization=mvn-app-org -Dsonar.host.url=https://sonarcloud.io -Dsonar.token=866ffb9787fb66bd47b589b776035cdfd84c0f2e -X'
                }
            }
        }
    }
}