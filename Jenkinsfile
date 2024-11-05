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
    }
}
