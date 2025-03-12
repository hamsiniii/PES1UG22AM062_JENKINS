pipeline {
    agent any
    
    stages {
        stage('Clone Repository') {
            steps {
                checkout([
                    $class: 'GitSCM', 
                    branches: [[name: '*/main']], 
                    userRemoteConfigs: [[
                        url: 'https://github.com/hamsiniii/PES1UG22AM062-Jenkins.git',
                        credentialsId: 'github-credentials-id'
                    ]]
                ])
            }
        }
        
        stage('Build') {
            steps {
                script {
                    build 'PES1UG22AM062-1'
                    sh 'g++ new.cpp -o output'
                }
            }
        }
        
        stage('Test') {
            steps {
                script {
                    sh './output'
                }
            }
        }
        
        stage('Deploy') {
            steps {
                script {
                    echo "Deploying..."
                }
            }
        }
    }
    
    post {
        success {
            echo 'Build and Deploy Successful!'
        }
        failure {
            echo 'Build Failed.'
        }
        always {
            echo 'Cleaning up...'
        }
    }
}
