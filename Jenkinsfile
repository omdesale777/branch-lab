pipeline {

    agent any

    stages {

        stage('Compile') {
            steps {
                echo "Building branch: ${env.BRANCH_NAME}"
            }
        }

        stage('Inspect') {
            steps {
                echo "Running checks for ${env.BRANCH_NAME}"
            }
        }

    }

}
