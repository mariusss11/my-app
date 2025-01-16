pipeline {
    agent any

    tools {
       maven '3.9.9'
    }

    stages {
        stage('---clean---') {
            steps {
                sh '''
                    ls -la
                    mvn clean
                    ls -la
                '''
            }
        }

        stage('---compile---') {
            steps {
                sh 'mvn compile'
            }
        }

        stage('---test---') {
            steps {
                sh 'mvn test'
            }
        }
        stage('---package---') {
            steps {
                sh '''
                    mvn package
                    ls -la
                '''
            }
        }       
    }
    post {
        always {
            junit 'target/surefire-reports/TEST-com.mycompany.app.AppTest.xml'
        }
        success {
            mail to: 'mariuscarchilan07@gmail.com',
            subject: "Successfull Pipeline: ${currentBuild.fullDisplayName}",
            body: "Everythins is good ${env.BUILD_URL}"
        }
    }
}