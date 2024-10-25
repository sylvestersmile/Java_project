pipeline {
    agent any

    stages {
        stage('Clone') {
            steps {
                // Corrected the cloning step
                git url: 'https://github.com/sylvestersmile/Java_project.git'
            }
        }
        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
        stage('Deploy') {
            steps {
                sh '''
                # Deploy the application to a local server (assumes a Spring Boot application)
                mvn spring-boot:run
                '''
            }
        }
    }

    post {
        always {
            archiveArtifacts artifacts: '**/target/*.jar', allowEmptyArchive: true
        }
    }
}
