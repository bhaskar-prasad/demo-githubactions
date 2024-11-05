pipeline {
    agent any
    environment {
        PATH = "C:\\Users\\bhaskar.prasad\\AppData\\Local\\Programs\\Python\\Python312;C:\\Users\\bhaskar.prasad\\AppData\\Local\\Programs\\Python\\Python312\\Scripts;${env.PATH}"
    }
    stages {
        stage('Clone Repository') {
            steps {
                git url: 'https://github.com/bhaskar-prasad/demo-githubactions', branch: 'main'
            }
        }

        stage('Install Dependencies') {
            steps {
                bat '''
                    python -m pip install --upgrade pip
                    python -m pip install pytest
                '''
            }
        }

        stage('Run Tests') {
            steps {
                bat 'python -m pytest test_main.py'
            }
        }
    }

    post {
        always {
            echo 'Build finished'
        }

        success {
            mail to: 'bhaskars.co@gmail.com',
                 subject: "Jenkins Build Successful: ${env.JOB_NAME",
                 body: "Good news! The Jenkins build for job ${env.JOB_NAME} completed successfully.\nCheck it at ${env.BUILD_URL}"
        }

        failure {
            mail to: 'bhaskars.co@gmail.com',
                 subject: "Jenkins Build Failed: ${env.JOB_NAME} ",
                 body: "Unfortunately, the Jenkins build for job ${env.JOB_NAME}  failed.\nCheck it at ${env.BUILD_URL}"
        }
    }
}
