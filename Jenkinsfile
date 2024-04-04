pipeline {
    agent any
    stages{
        stage("Build step 1") {
            steps {
                sh 'echo "Build step 1"'
            }
        }
        stage("SSH to bastionhost") {
            steps {
                sshagent(credentials: ['rockylite']) {
                    sh '''
                        [ -d ~/.ssh ] || mkdir ~/.ssh && chmod 0700 ~/.ssh
                        ssh bastion 'ip a'
                    '''
                }
            }
        }


        stage('SSH to devserver and execute build scripts') {
            steps {
                script {
                    sh """ssh -tt private << EOF
                    sudo su - admin
                    whoami
                    exit
                    exit
                    exit
                    << EOF
                    """
                }
            }
        }
    }
}
