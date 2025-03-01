pipeline {
    agent any
    
    environment {
        AWS_ACCESS_KEY_ID = credentials('aws-jenkins-integration')
    }
    stages {
        stage('Code checkout from Git') {
            steps {
                checkout([
                    $class: 'GitSCM',
                    branches: [[name: '*/main']],
                    extensions: [],
                    userRemoteConfigs: [[
                        credentialsId: 'jenkins-git-integration',
                        url: 'https://github.com/arunawsdevops/terraform-test-run-jenkins'
                    ]]
                ])
            }
        }

        stage('terraform init') {
            steps {
                script {
                    sh "terraform init"
                }
            }
        }
    }
}
