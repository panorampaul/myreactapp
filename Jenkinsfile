pipeline {
    agent any

    tools {
        nodejs "node16.9"
        jdk "jdk_17"
        maven "maven3.9.0"
        dockerTool "docker"
        }

    stages {

        stage ("Install Pulumi") {
            steps {
                sh "curl -fsSL https://get.pulumi.com | sh"
                sh "$HOME/.pulumi/bin/pulumi version"
            }
        }

          stage('Read PULUMI_TOKEN from aws secrets') {
            steps {
                script {
                    PULUMI_RESPONSE = sh(returnStdout: true, script: 'aws secretsmanager get-secret-value --secret-id pulumi_devops_account_user_token')
                }
                script {
                    def props = readJSON text: PULUMI_RESPONSE
                    PULUMI_ACCESS_TOKEN = props['SecretString']
                }
                script {
                    sh "pulumi whoami"
                }

            }

        }

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

        stage('Check Docker') {
            steps {
                sh 'which docker'
                sh 'docker --version'
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

        stage('Check aws') {
            steps {
                sh 'which aws'
                sh 'aws --version'
                sh 'aws eks describe-cluster --name devstack-eksCluster-af87597'
            }
        }

        stage('Check kubectl') {
            steps {
                sh 'which kubectl'
                //sh 'kubectl version' //this returns an error if not logged in
            }
        }

    }
}