
pipeline {

    agent {
        label 'Agent1'
    }

    stages {

        stage('Hello Jenkins') {

            steps {
                sh 'echo "Welcome to Notes CI Pipeline"'
            }

        }

        stage('Workspace Information') {

            steps {
                sh 'pwd'
                sh 'whoami'
                sh 'hostname'
                sh 'ls -la'
            }

        }

        stage('Git Checkout') {

            steps {
                checkout scm
            }

        }

        stage('Verify Checkout') {

            steps {
                sh 'echo "Checking downloaded source code"'
                sh 'ls -la'
                sh 'git log -1 --oneline'
            }

        }

    }

    post {

        success {
            echo 'Lab 2 completed successfully'
        }

        failure {
            echo 'Lab 2 failed. Check console output'
        }

    }

}
