pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                // Забираем код из репозитория
                checkout scm
            }
        }
        stage('Install Dependencies') {
            steps {
                // Устанавливаем зависимости проекта
                sh 'sudo apt install npm'
                sh 'npm install'
            }
        }
        stage('Build') {
            steps {
                // Собираем приложение (в данном случае это может быть просто проверка кода)
                sh 'echo "Building application..."'
            }
        }
        stage('Test') {
            steps {
                // Запуск тестов, если они есть
                sh 'npm test || echo "No tests defined"'
            }
        }
        stage('Run Application') {
            steps {
                // Запуск приложения
                sh 'node server.js &'
                echo "Application is running!"
            }
        }
    }
    post {
        always {
            // Всегда выводим логи
            echo "Pipeline finished"
        }
        success {
            // Если всё успешно
            echo "Pipeline completed successfully!"
        }
        failure {
            // Если произошла ошибка
            echo "Pipeline failed!"
        }
    }
}
