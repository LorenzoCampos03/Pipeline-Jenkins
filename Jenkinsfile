pipeline {
    agent any

    environment {
        // El canal se define en la configuración global o aquí

    stages {
        stage('Initialize') {
            steps {
                script {
                    env.PROJECT_NAME = 'Pipeline-Jenkins'
                    def fecha = new Date().format('yyyy-MM-dd HH:mm:ss')
                    slackSend channel: '#notificaciones-dev', message: "*${env.PROJECT_NAME}* - Build iniciado :hammer_and_wrench: \nFecha: ${fecha}"
                }
                sh 'echo "Ejecutando compilación en Arch Linux..."'
            }
        }
        stage('Build') {
            steps {
                    bat 'echo Ejecutando compilación en Windows...'
                    def fecha = new Date().format('yyyy-MM-dd HH:mm:ss')
                    slackSend channel: '#notificaciones-dev', message: "*${env.PROJECT_NAME}* - Test iniciado :test_tube: \nFecha: ${fecha}"
                }
                sh 'true' 
                sh 'echo "Ejecutando compilación en Arch Linux..."'
            }
        }
        stage('Test') {
                    bat 'echo Prueba simulada exitosa'
            script {
                def fecha = new Date().format('yyyy-MM-dd HH:mm:ss')
                slackSend channel: '#notificaciones-dev', message: "*${env.PROJECT_NAME}* - Pipeline iniciado :rocket: \nFecha: ${fecha}"
            }
                echo 'Ejecutando pruebas unitarias...'
                // Cambiar a 'false' para probar la notificación de error
            script {
                def fecha = new Date().format('yyyy-MM-dd HH:mm:ss')
                slackSend channel: '#notificaciones-dev', message: "*${env.PROJECT_NAME}* - Éxito :white_check_mark: \nFecha: ${fecha}"
            }
                sh 'true' 
            }
            script {
                def fecha = new Date().format('yyyy-MM-dd HH:mm:ss')
                slackSend channel: '#notificaciones-dev', message: "*${env.PROJECT_NAME}* - Fallo :x: \nFecha: ${fecha}"
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