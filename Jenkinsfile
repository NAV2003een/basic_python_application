pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main', url: 'https://github.com/NAV2003een/basic_python_application.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                bat 'python --version'
                bat 'python -m pip install --upgrade pip'
                bat 'python -m pip install -r requirements.txt'
            }
        }

        stage('Build') {
            steps {
                bat '''
                if not exist dist (
                    mkdir dist
                )
                copy *.py dist\\
                python -m compileall dist
                '''
            }
        }

        stage('Run Tests') {
            steps {
                bat 'python -m unittest discover'
            }
        }
    }
}
