pipeline {
    agent { label 'jenkins-agent1' }

    tools {
        jdk 'Jdk17'
        maven 'maven3'
    }

    stages {
        stage('Clean Workspace') {
            steps {
                cleanWs()
            }
        }

        stage('Checkout Code') {
            steps {
                git url: 'https://github.com/poojabharambe18/maven-projects.git', branch: 'master'
            }
        }

        stage('SonarQube Scan') {
            steps {
                withSonarQubeEnv('sonarqube') {
                    sh 'mvn sonar:sonar -U'
                }
            }
        }

        stage('Build with Maven') {
            steps {
                sh 'mvn clean package -U'
            }
        }
    }
}
