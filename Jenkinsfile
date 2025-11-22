def flag = true   // or false

pipeline {
    agent any

    parameters {
        // these are types of parameters (from screenshot)
        string(name: 'VERSION', defaultValue: '', description: 'version to deploy on prod')
        choice(name: 'VERSIONS', choices: ['1.1.0', '1.2.0', '1.3.0'], description: '')
        booleanParam(name: 'executeTests', defaultValue: true, description: '')
    }

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
                bat "mvn -v"
            }
        }

        stage('test') {
            when {
                expression {
                    params.executeTests   // <-- EXACTLY as screenshot required
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
