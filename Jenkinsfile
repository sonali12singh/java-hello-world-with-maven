pipeline{
    agent any

    tools {
         maven 'maven'
         jdk 'java'
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'master', url: 'https://github.com/sonali12singh/java-hello-world-with-maven.git'
            }
        }

        stage('Build') {
            steps {
                echo "Building the code..."
        
                sh 'mvn clean package'
            }
        }

        stage('Test') {
            steps {
                echo "Running unit tests..."
                sh 'mvn test'
            }
        }

        stage('Deploy to QA') {
            steps {
                echo "Deploying to QA environment..."
                //Deploy to your QA node (if configured)
            }
        }
    }
       
    post {
        success {
            echo "Build Successful! "
        }
        failure {
            echo "Build Failed "
            mail to: 'sonaliinindiaa@gmail.com',
                 subject: "Build Failed: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                 body: "The build failed. Check Jenkins console output at ${env.BUILD_URL} for details."
        }
    }
}
