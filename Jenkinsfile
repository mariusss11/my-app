pipeline {
    agent any

    tools {
       maven '3.9.9'
    }

    stages {
        stage('---clean---') {
            steps {
                sh 'mvn clean'
            }
        }

        stage('---compile---') {
            steps {
                sh 'mvn package'
            }
        }

        stage('---test---') {
            steps {
                sh 'mvn test'
            }
        }
        stage('---package---') {
            steps {
                sh 'mvn package'
            }
        }

        
    }
}