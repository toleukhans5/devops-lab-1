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
                sh '''
                    echo "=== FILES ==="
                    ls -la

                    if [ -f Dockerfile ]; then
                        echo "Dockerfile найден"
                    else
                        echo "Dockerfile НЕ найден"
                    fi

                    if [ -f requirements.txt ]; then
                        echo "requirements.txt найден"
                    else
                        echo "requirements.txt НЕ найден"
                    fi

                    if [ -d src ]; then
                        echo "Папка src найдена"
                        if [ -f src/app.py ]; then
                            echo "Файл src/app.py найден"
                        else
                            echo "Файл src/app.py НЕ найден"
                        fi
                    else
                        echo "Папка src НЕ найдена"
                    fi

                    if [ -f .dockerignore ]; then
                        echo ".dockerignore найден"
                    else
                        echo ".dockerignore НЕ найден"
                    fi
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

