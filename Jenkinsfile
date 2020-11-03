pipeline {
    agent none
    stages {
        stage('Build') {
            agent {
                label 'docker'
                docker {
                    image 'python:3-alpine'
                }
            }
            steps {
                withEnv(["HOME=${env.WORKSPACE}"]) {
                    sh 'pip install --user -r requirements.txt'
                    sh 'python app.py'
                }
            }
            post {
                always {
                    junit 'output.xml'
                }
            }
        }
    }
}
