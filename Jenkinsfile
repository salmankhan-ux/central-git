pipeline {
    agent any

    stages {
        stage('Deploy') {
            steps {
                sshagent(['ec2-server-key']) {
                    sh """
                        ssh -o StrictHostKeyChecking=no ec2-user@13.51.171.237 '/home/ec2-user/myapp/deploy.sh'
                    """
                }
            }
        }
    }
}
