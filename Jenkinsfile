pipeline {
    agent any

    tools {
        maven 'Maven 3.8.1' // must match Maven tool name in Jenkins config
    }

    environment {
        BUILD_DIR = 'target'
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/your-user/your-java-repo.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean compile'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Package') {
            steps {
                sh 'mvn package'
            }
        }

        stage('Archive Artifacts') {
            steps {
                archiveArtifacts artifacts: "${BUILD_DIR}/*.jar", fingerprint: true
            }
        }
    }

    post {
        success {
            echo 'Build succeeded!'
        }
        failure {
            echo 'Build failed.'
        }
    }
}
