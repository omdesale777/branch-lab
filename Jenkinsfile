pipeline {
    agent any
    parameters {
        choice(
            name: 'ENVIRONMENT',
            choices: ['staging', 'production'],
            description: 'Choose deployment environment'
        )
    }
    stages {
        stage('Build') {
            steps {
                echo 'Building application...'
            }
        }
        stage('Test') {
            steps {
                echo 'Executing validation tests...'
            }
        }
        stage('Deploy') {
            steps {
                echo "Deploying application to ${params.ENVIRONMENT}"
            }
        }
    }
    post {
        success {
            echo 'Deployment pipeline completed successfully.'
        }
        failure {
            echo 'Deployment pipeline failed.'
        }
    }
}
