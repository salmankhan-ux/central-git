pipeline {
    agent any

    environment {
        EC2_IP = '13.51.171.237'
        SSH_KEY = '/var/lib/jenkins/.ssh/my-key.pem'
    }

    stages {
        stage('Connect to EC2') {
            steps {
                sh """
                ssh -o StrictHostKeyChecking=no -i ${SSH_KEY} ec2-user@${EC2_IP} "echo Connected from Jenkins"
                """
            }
        }

        stage('Run Docker Command') {
            steps {
                sh """
                ssh -o StrictHostKeyChecking=no -i ${SSH_KEY} ec2-user@${EC2_IP} "docker ps && docker run --rm hello-world"
                """
            }
        }
    }
}
