pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building the application...'
            }
        }

        stage('Deploy') {
            steps {
                script {
                    def dockerCmd = "docker run --rm hello-world"

                    sshagent(['ec2-server-key']) {
                        sh """
                            ssh -o StrictHostKeyChecking=no ec2-user@13.51.171.237 '${dockerCmd}'
                        """
                    }
                }
            }
        }
    }
}
