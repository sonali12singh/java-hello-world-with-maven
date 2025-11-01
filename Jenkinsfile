pipeline{
    agent any

    tools {
         maven 'maven'
         jdk 'java'
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/sonali12singh/java-hello-world-with-maven.git'
            }
        }

        stage('Build') {
            steps {
                echo "Building the code..."
                // Example for Maven:
                // sh 'mvn clean package'
            }
        }

        stage('Test') {
            steps {
                echo "Running unit tests..."
                // sh 'mvn test'
            }
        }

        stage('Deploy to QA') {
            steps {
                echo "Deploying to QA environment..."
                // Deploy to your QA node (if configured)
            }
        }
    }

    post {
        success {
            echo "Build Successful! "
        }
        failure {
            echo "Build Failed "
        }
    }
}
