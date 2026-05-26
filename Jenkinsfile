pipeline {
    agent any

    parameters {
        string(
            name: 'PERSON',
            defaultValue: 'Mr Jenkins',
            description: 'Who should I say hello to?'
        )

        text(
            name: 'BIOGRAPHY',
            defaultValue: '',
            description: 'Enter some information about the person'
        )

        booleanParam(
            name: 'TOGGLE',
            defaultValue: true,
            description: 'Toggle this value'
        )

        choice(
            name: 'CHOICE',
            choices: ['One', 'Two', 'Three'],
            description: 'Pick something'
        )

        password(
            name: 'PASSWORD',
            defaultValue: 'SECRET',
            description: 'Enter a password'
        )
    }

    stages {

        stage('Build') {
            steps {
                sh 'echo it is build stage'
            }
        }




        stage('Approval') {
            input {
                message "Should we continue?"
                ok "Yes, we should."
                submitter "alice,bob"

                parameters {
                    string(
                        name: 'APPROVER_NAME',
                        defaultValue: 'Mr Jenkins',
                        description: 'Who approved the pipeline?'
                    )
                }
            }

            steps {
                echo "Approval received"
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

        stage('Print Parameters') {
            steps {
                echo "Hello ${params.PERSON}"
                echo "Biography: ${params.BIOGRAPHY}"
                echo "Toggle value: ${params.TOGGLE}"
                echo "My choice is: ${params.CHOICE}"
                echo "Password is: ${params.PASSWORD}"
            }
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