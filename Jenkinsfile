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