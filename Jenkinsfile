pipeline{
    agent any

    tools {
         maven 'maven'
         jdk 'java'
    }

    stages{
        stage('checkout'){
            steps{
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[credentialsId: 'github access', url: 'https://github.com/sreenivas449/java-hello-world-with-maven.git']]])
            }
        }
        stage('build'){
            steps{
               sh  'mvn clean package'
            }
        }
        stage('Test'){
            steps{
                sh "Running unit test"
                sh "mvn test"
            }
        }
        stage('Deploy to Qa ENv'){
            steps{
                echo "Deploying to QA ENV"
            }
        }
        post{
            success{
                echo "Build is success"
            }
            failure{
                echo "build failed"
            }
    }
}
