pipeline {
    agent any
    parameters {
        choice(
            name: 'ENVIRONMENT',
            choices: ['staging','production'],
            description: 'Target Environment'
        )
    }
    environment {
        APP_NAME = 'demo-app'
    }
    stages {
        stage('Build') {
            steps {
                echo 'Building ${env.APP_NAME}'
            }
        }
        stage('Tests') {
            parallel {
                stage('Unit') {
                    steps {
                        sh 'echo Running unit tests'
                    }
                }
		stage('Integration') {
                    steps {
                        sh 'echo Running integration tests'
		    }
	        }
	    }
        }
	stage('Approve') {
            when {
                expression { params.ENVIRONMENT == production }
            }
            steps {
                input message: 'Deploy to production?'
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
