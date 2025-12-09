pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/damiguet/jenkins-java.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn -B clean compile'
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
    }

    post {
        success {
            archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
            echo 'Build y empaquetado finalizado con éxito.'
        }
        failure {
            echo 'El pipeline falló.'
        }
    }
}
