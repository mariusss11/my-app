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
            subject: "Pipeline Success: ${currentBuild.fullDisplayName}",
            body: """\
            Hello,

            The pipeline run '${currentBuild.fullDisplayName}' was successful!

            Details:
            - Build URL: ${env.BUILD_URL}
            - Build Status: Successful

            Debuggin:
            - Env: ${env}
            - CurrentBuild: ${currentBuild}

            Everything is working as expected. If you have any questions, feel free to reach out.

            Best regards,
            Your CI/CD System
            """
        }
    }
}