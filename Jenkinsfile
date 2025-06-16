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
                bat '"C:\\Users\\HP\\AppData\\Local\\Programs\\Python\\Python311\\python.exe" --version'
                bat '"C:\\Users\\HP\\AppData\\Local\\Programs\\Python\\Python311\\python.exe" -m pip install --upgrade pip'
                bat '"C:\\Users\\HP\\AppData\\Local\\Programs\\Python\\Python311\\python.exe" -m pip install -r requirements.txt'
            }
        }

        stage('Build') {
            steps {
                bat '''
                if not exist dist mkdir dist
                copy *.py dist\\
                "C:\\Users\\HP\\AppData\\Local\\Programs\\Python\\Python311\\python.exe" -m compileall dist
                '''
            }
        }

        stage('Run Tests') {
            steps {
                bat '"C:\\Users\\HP\\AppData\\Local\\Programs\\Python\\Python311\\python.exe" -m unittest discover'
            }
        }
    }
}
