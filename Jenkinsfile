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

        stage('Which Java?') {
            steps {
                sh 'java --version'
            }
        }

         stage('Java Home?') {
            steps {
                sh 'echo $JAVA_HOME'
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