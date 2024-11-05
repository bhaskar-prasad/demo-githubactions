pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                git url: 'https://github.com/bhaskar-prasad/demo-githubactions', branch: 'main'
            }
        }

        stage('Install Dependencies') {
            steps {
                // Use 'bat' for Windows, 'sh' for Linux/Mac
                bat '''
                    python -m pip install --upgrade pip
                    pip install pytest
                '''
            }
        }

        stage('Run Tests') {
            steps {
                // Again, use 'bat' for Windows
                bat 'pytest test_main.py'
            }
        }
    }

    post {
        always {
            echo 'Build finished'
        }
    }
}
