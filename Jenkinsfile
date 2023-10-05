pipeline {
    agent {
        label 'ansible-server'
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Patch Server') {
            steps {
                script {
                    // Set the home directory for the job
                    def homeDir = '/home/ec2-user/ansible-dev'

                    // Run the Ansible playbook to patch the server
                    sh "ansible-playbook patch.yml"
                }
            }
        }
    }

    post {
        success {
            echo 'Server patching successful'
        }
        failure {
            echo 'Server patching failed'
            // You can take additional actions here in case of failure
        }
    }
}

