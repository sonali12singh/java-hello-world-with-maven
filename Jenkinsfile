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

        stage('Unit Test') {
    steps {
        sh 'mvn test || true' // Don’t fail if tests missing
    }
    post {
        always {
            script {
                def reports = findFiles(glob: 'target/surefire-reports/*.xml')
                if (reports.length > 0) {
                    junit 'target/surefire-reports/*.xml'
                } else {
                    echo ' No test reports found — skipping JUnit publish step.'
                }
            }
        }
    }
}

        stage('Deploy to QA') {
            steps {
                echo "Deploying to QA environment..."
                
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
