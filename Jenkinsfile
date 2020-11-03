pipeline {
//None parameter in the agent section means that no global agent will be allocated for the entire Pipeline’s
//execution and that each stage directive must specify its own agent section.
    agent none
    
    stage('Build environment') {
            steps {
                echo "Building virtualenv"
                sh  ''' 
                    pip install -r requirements.txt
                '''
            }
    }
    stages {
        stage('Build') {
            agent {
                label 'docker'
            }
            steps {
                //This sh step runs the Python command to compile your application and
                //its calc library into byte code files, which are placed into the sources workspace directory
                sh 'pytest'
            }
        }
    }
       
}
