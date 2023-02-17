pipeline {
    agent any

    tools {nodejs "node16.9"}

    stages {
        stage("Clone code") {
            steps {
                script {
                    checkout scm
                }
            }
        }

        stage('Which Java?') {
            steps {
                sh 'java --version'
            }
        }

        stage('Which MVN?') {
            steps {
                sh 'mvn --version'
            }
        }

        stage("npm install") {
            steps {
              sh "npm install"
            }
        }

        stage("build") {
            steps {
              sh "npm run build"
            }
        }

    }
}