pipeline {
    agent any

    tools {nodejs "nodejs"}

    stages {
        stage("Clone code") {
            steps {
                script {
                    checkout scm
                }
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