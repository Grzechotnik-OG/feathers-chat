pipeline {
    agent any

    stages {
        stage('Build & Test') {
            steps {
                echo 'Building & testing ...'
                sh 'docker-compose up'
            }
        }
    }
    post {
        success {
            emailext attachLog: true,
                subject: 'Pipeline ${env.JOB_NAME} succeded',
                body: 'Job ${env.JOB_NAME} ${currentBuild.currentResult}: build ${env.BUILD_DISPLAY_NAME}',
                to: 'grzesiekc188@gmail.com'
        }
        failure {
            emailext attachLog: true,
                subject: 'Pipeline ${env.JOB_NAME} failed',
                body: 'Job ${env.JOB_NAME} ${currentBuild.currentResult}: build ${env.BUILD_DISPLAY_NAME}',
                to: 'grzesiekc188@gmail.com'
        }
    }
}
