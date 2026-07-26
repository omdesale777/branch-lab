pipeline {
    agent any
    parameters {
        choice(
            name: 'ENVIRONMENT', choices: ['staging', 'production'], description: 'Target Environment')
    }
    environment {
        APP_NAME = 'demo-app'
    }
	    stages {
	        stage('Build') {
		    	steps {
		        echo "Building ${env.APP_NAME}"
		    	}
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
                        sh 'echo Integration tests running'
		    	}
	        }
	    }
    }
	stage('Approve') {
    	when {
        	expression { params.ENVIRONMENT =='production' }
    	}
    	steps {
        	input message: 'Deploy to Production?'
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
            echo 'Pipeline Succeeded'
        }
        failure {
            echo 'Pipeline Failed.'
        }
}
