def flag = true  // or false

pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building Project'
            }
        }

        stage('Test') {
            when {
                expression {
                    flag == false   // Test stage runs only when flag is false
                }
            }
            steps {
                echo 'Testing Project'
            }
        }

        stage('Deploy') {
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
