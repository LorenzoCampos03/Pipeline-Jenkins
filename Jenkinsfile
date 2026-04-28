pipeline {
    agent any

    environment {
        // El canal se define en la configuración global o aquí
        SLACK_CHANNEL = '#jenkins-notificaciones'
    }

    stages {
        stage('Initialize') {
            steps {
                slackSend(color: '#FFFF00', message: "🚀 Iniciando Pipeline: ${env.JOB_NAME} (Build #${env.BUILD_NUMBER})")
            }
        }
        stage('Build') {
            steps {
                echo 'Compilando el proyecto...'
                sh 'echo "Ejecutando compilación en Arch Linux..."'
            }
        }
        stage('Test') {
            steps {
                echo 'Ejecutando pruebas unitarias...'
                // Cambiar a 'false' para probar la notificación de error
                sh 'true' 
            }
        }
    }

    post {
        success {
            slackSend(
                color: '#36a64f',
                message: "✅ ÉXITO: ${env.JOB_NAME} \nBuild: ${env.BUILD_NUMBER} \nEstado: COMPLETADO"
            )
        }
        failure {
            slackSend(
                color: '#ff0000',
                message: "❌ ERROR: ${env.JOB_NAME} \nBuild: ${env.BUILD_NUMBER} \nRevisa los logs en: ${env.BUILD_URL}"
            )
        }
    }
}