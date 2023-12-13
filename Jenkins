pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Check out the code from your version control system
                checkout scm
            }
        }

        stage('Build') {
            steps {
                // In this stage, you might perform any necessary build steps.
                // For an HTML project, this might include copying files or running a build tool like npm, yarn, or others.
                // For simplicity, let's just copy the HTML files to the build directory.
                sh 'mkdir -p build'
                sh 'cp -r * build/'
            }
        }

        stage('Deploy') {
            steps {
                // Here, you could deploy your HTML files to a web server or hosting service.
                // For demonstration purposes, let's assume you are copying files to a server via SSH.
                // Make sure to replace 'your-server' and 'your-ssh-credentials-id' with your actual server information.
                sh 'sshpass -p your-ssh-password scp -r build/* your-ssh-user@your-server:/path/to/deployment/directory'
            }
        }
    }

    post {
        success {
            echo 'Pipeline succeeded! Your HTML project has been built and deployed.'
        }
        failure {
            echo 'Pipeline failed. Please check the Jenkins console output for details.'
        }
    }
}
