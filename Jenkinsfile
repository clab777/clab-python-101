pipeline {
    agent none
    stages {
        stage('Build') {
            agent {
               label 'docker'
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
