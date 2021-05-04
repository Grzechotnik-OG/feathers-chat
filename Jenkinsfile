pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building...'
                sh 'npm install'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing...'
                sh 'npm test'
            }
        }
    }
    post {
        success {
            emailext subject: 'Pipeline ${env.JOB_NAME} succeded',
                body: 'Job ${env.JOB_NAME} ${currentBuild.currentResult}, build ${env.BUILD_DISPLAY_NAME}',
                attachLog: true,
                to: 'grzesiekc188@gmail.com'
        }
        failure {
            emailext subject: 'Pipeline ${env.JOB_NAME} failed',
                body: 'Job ${env.JOB_NAME} ${currentBuild.currentResult}, build ${env.BUILD_DISPLAY_NAME}',
                attachLog: true,
                to: 'grzesiekc188@gmail.com'
        }
    }
}
