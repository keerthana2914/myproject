pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'gcc hello.c -o hello'
            }
        }

        stage('Test') {
            steps {
                sh './hello'
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                    mkdir -p deployment
                    cp hello deployment/
                '''
            }
        }
    }

    post {
        success {
            archiveArtifacts artifacts: 'deployment/**'
        }
    }
}
