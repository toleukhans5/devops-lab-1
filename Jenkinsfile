pipeline {
    agent any

    stages {

        stage('Checkout Code') {
            steps {
                echo 'Забираем код из GitHub...'
                checkout scm
            }
        }

        stage('Check Files') {
            steps {
                echo 'Проверяем созданные файлы...'
                bat '''
                    echo === FILES IN REPO ===
                    dir

                    IF EXIST Dockerfile (
                        echo Dockerfile найден
                    ) ELSE (
                        echo Dockerfile НЕ найден
                    )

                    IF EXIST requirements.txt (
                        echo requirements.txt найден
                    ) ELSE (
                        echo requirements.txt НЕ найден
                    )

                    IF EXIST src (
                        echo Папка src найдена
                        IF EXIST src\\app.py (
                            echo Файл src\\app.py найден
                        ) ELSE (
                            echo Файл src\\app.py НЕ найден
                        )
                    ) ELSE (
                        echo Папка src НЕ найдена
                    )

                    IF EXIST .dockerignore (
                        echo .dockerignore найден
                    ) ELSE (
                        echo .dockerignore НЕ найден
                    )
                '''
            }
        }

        stage('Docker Theory') {
            steps {
                echo 'ТЕОРИЯ DOCKER'
                echo 'docker build -t my-app .'
                echo 'docker run -d -p 8081:5000 my-app'
                echo 'curl http://localhost:8081/health'
            }
        }
    }

    post {
        success {
            echo 'SUCCESS: CI/CD пайплайн орындалды!'
        }
        failure {
            echo 'FAIL: Қате шықты, бірақ бұл да тәжірибе.'
        }
    }
}
