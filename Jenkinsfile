     pipeline {
    agent any

    tools {
        git 'git' 
    }

    stages {
        stage('Checkout Code') {
            steps {
                git url: 'https://github.com/poojabharambe18/maven-projects.git'
            }
        }

        stage('Build & SonarQube') {
            steps {
                withSonarQubeEnv('sonarqube') {
                    sh 'mvn clean package sonar:sonar'
                }
            }
        }
    }
}

