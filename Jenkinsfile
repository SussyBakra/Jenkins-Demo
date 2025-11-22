def flag = true   // or false

pipeline {
    agent any

    tools {
        maven 'Maven'   // Tool configured in Jenkins > Global Tool Configuration
    }

    environment {
        // variables defined here can be used by any stage
        NEW_VERSION = '1.3.0'
    }

    stages {

        stage('build') {
            steps {
                echo 'Building Project'

                // using environment variable
                echo "Building version ${NEW_VERSION}"

                // Windows uses bat, NOT sh
                bat "mvn install"
            }
        }

        stage('test') {
            when {
                expression {
                    flag == false   // test stage runs only when flag is false
                }
            }
            steps {
                echo 'Testing Project'
            }
        }

        stage('deploy') {
            steps {
                echo 'Deploying Project'
            }
        }
    }

    post {
        always {
            echo 'Post build condition running'
        }
        failure {
            echo 'Post Action if Build Failed'
        }
    }
}
