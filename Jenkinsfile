pipeline {
    agent any

    tools {
        nodejs "node16.9"
        jdk "jdk_17"
        maven "maven3.9.0"
        }

    stages {
        stage("Clone code") {
            steps {
                script {
                    checkout scm
                }
            }
        }

        stage('Check Java') {
            steps {
                sh 'which java'
                sh 'which javac'
                sh 'java --version'
            }
        }

        stage('Check MVN') {
            steps {
                sh 'which mvn'
                sh 'mvn --version'
            }
        }

         stage('Check node/npm') {
            steps {
                sh 'which node'
                sh 'which npm'
                sh 'node --version'
                sh 'npm --version'
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