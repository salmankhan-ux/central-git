pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building the application...'
            }
        }

        stage('Connect to EC2') {
            steps {
                sshagent(['ec2-server-key']) {
                    sh """
                        ssh -o StrictHostKeyChecking=no \
                        ec2-user@13.51.171.237 \
                        "echo Connected from Jenkins"
                    """
                }
            }
        }

        stage('Run Docker Command') {
            steps {
                sshagent(['ec2-server-key']) {
                    sh """
                        ssh -o StrictHostKeyChecking=no \
                        ec2-user@13.51.171.237 \
                        "docker run --rm hello-world"
                    """
                }
            }
        }
    }
}
