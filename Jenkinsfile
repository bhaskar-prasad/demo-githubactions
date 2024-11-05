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
                sh '''
                    pip install pytest
                '''
            }
        }

        stage('Run Tests') {
            steps {
                sh 'pytest test_main.py'
            }
        }
    }

    post {
        always {
            echo 'Build finished'
        }
    }
}
