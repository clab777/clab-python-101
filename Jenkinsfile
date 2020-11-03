pipeline {
//None parameter in the agent section means that no global agent will be allocated for the entire Pipeline’s
//execution and that each stage directive must specify its own agent section.
    agent none

    stages {
            
        stage('Build environment') {
            agent {
                label 'docker'
            }

            steps {
                    echo "Building virtualenv"
                    sh  ''' 
                        sudo easy_install pip
                        pip install -r requirements.txt
                    '''
                }
        }
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
