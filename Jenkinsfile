pipeline {
    agent {
        label 'Agent-1'
    }

    stages {

        stage('Build') {
            steps {
                sh 'echo it is build stage'
            }
        }

        stage('Test') {
            steps {
                sh 'echo this is test stage'
            }
        }

        stage('Deploy') {
            steps {
                sh 'echo this is deploy stage'
            }
        }
    }

    post {
        always {
            echo 'I will always run this session'
        }

        success {
            echo 'I will run only when pipeline succeeds'
        }

        failure {
            echo 'I will run only when pipeline fails'
        }
    }
}