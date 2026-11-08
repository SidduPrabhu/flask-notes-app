
pipeline {

    agent {
        label 'Agent1'
    }

    parameters {

        choice(
            name: 'ENVIRONMENT',
            choices: ['dev', 'qa', 'prod'],
            description: 'Select deployment environment'
        )

        string(
            name: 'IMAGE_TAG',
            defaultValue: 'v1.0',
            description: 'Enter Docker image tag'
        )

        booleanParam(
            name: 'RUN_TESTS',
            defaultValue: true,
            description: 'Run automated tests'
        )

    }

    environment {

        APP_NAME = 'notes-api'

        DOCKER_NAMESPACE = 'your-dockerhub-username'

    }

    stages {

        stage('Display Configuration') {

            steps {

                echo "Environment: ${params.ENVIRONMENT}"

                echo "Image Tag: ${params.IMAGE_TAG}"

                echo "Run Tests: ${params.RUN_TESTS}"

                echo "Application: ${env.APP_NAME}"

                echo "Docker Namespace: ${env.DOCKER_NAMESPACE}"

            }

        }

        stage('Validate Parameters') {

            steps {

                script {

                    if (params.IMAGE_TAG == '') {

                        error('Docker image tag cannot be empty')

                    }

                    if (
                        params.ENVIRONMENT == 'prod' &&
                        params.RUN_TESTS == false
                    ) {

                        error('Production deployment requires tests')

                    }

                }

            }

        }

        stage('Application Information') {

            steps {

                script {

                    def imageName =
                        "${env.DOCKER_NAMESPACE}/${env.APP_NAME}:${params.IMAGE_TAG}"

                    echo "Docker Image: ${imageName}"

                }

            }

        }

        stage('Test Execution') {

            when {

                expression {
                    params.RUN_TESTS == true
                }

            }

            steps {

                echo 'Executing automated tests...'

                sh 'python3 --version'

            }

        }

    }

    post {

        success {

            echo 'Pipeline completed successfully'

        }

        failure {

            echo 'Pipeline failed. Check the console output.'

        }

    }

}
