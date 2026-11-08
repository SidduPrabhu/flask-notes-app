pipeline {
    agent {
        label 'Agent1'
    }
    stages {
        stage('Hello Jenkins'){
            steps {
                sh 'echo "Hello from jenkins agent"'
            }
        }
        stage('Workspace Inforamtion'){
            steps {
                sh ''' 
                 pwd
                 whoami
                 hostname
                 ls -la
                 df -h
                 printenv
                '''
            }
        }
        
    }
}