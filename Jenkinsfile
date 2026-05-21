pipeline {
    agent {
        label 'Agent-1'
    }
    stages {
        stage('Build') {
            steps {
                sh 'echo it is buid stage'
                
            }
        }
        stage('Test') {
            steps {
                sh 'echo this is test stage'
                
            }
        }
        stage('deploy') {
            steps {
                sh 'echo this is deploy stage'
                
            }
    }
    }
}