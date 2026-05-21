pipeline {
    agent {
        label 'Agent-1'
    }
     parameters {
        string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')

        text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')

        booleanParam(name: 'TOGGLE', defaultValue: true, description: 'Toggle this value')

        choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')

        password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
    }
    stages {

        stage('Build') {
            steps {
                sh 'echo it is build stage'
            }
        }
        stage('approval') {
            input {
                message "Should we continue?"
                ok "Yes, we should."
                submitter "alice,bob"
                parameters {
                    string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
                }
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
        stage('print parameters') {
            steps {
                echo "Hello ${params.PERSON}"
                echo "Biography: ${params.BIOGRAPHY}"
                echo "Hello ${params.TOGGLE}"
                echo "my choice is: ${params.CHOICE}"
                echo "passord is:${params.PASSWORD} "
            }

        }
       

    post {
        always {
            echo "I will always run this session"
            deleteDir()
        }

        success {
            echo "I will run only when pipeline succeeds"
        }

        failure {
            echo "I will run only when pipeline fails"
        }
    }
}
}