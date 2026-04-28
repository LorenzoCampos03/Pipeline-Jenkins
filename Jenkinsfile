pipeline {
    agent any

    environment {
        PROJECT_NAME = 'Pipeline-Jenkins'
    }

    stages {
        stage('Build') {
            steps {
                script {
                    def fecha = new Date().format('yyyy-MM-dd HH:mm:ss')
                    slackSend channel: '#notificaciones-dev', message: "*${env.PROJECT_NAME}* - Build iniciado :hammer_and_wrench: \nFecha: ${fecha}"
                }
                bat 'echo Ejecutando compilación en Windows...'
            }
        }
        stage('Test') {
            steps {
                script {
                    def fecha = new Date().format('yyyy-MM-dd HH:mm:ss')
                    slackSend channel: '#notificaciones-dev', message: "*${env.PROJECT_NAME}* - Test iniciado :test_tube: \nFecha: ${fecha}"
                }
                bat 'echo Prueba simulada exitosa'
            }
        }
    }

    post {
        started {
            script {
                def fecha = new Date().format('yyyy-MM-dd HH:mm:ss')
                slackSend channel: '#notificaciones-dev', message: "*${env.PROJECT_NAME}* - Pipeline iniciado :rocket: \nFecha: ${fecha}"
            }
        }
        success {
            script {
                def fecha = new Date().format('yyyy-MM-dd HH:mm:ss')
                slackSend channel: '#notificaciones-dev', message: "*${env.PROJECT_NAME}* - Éxito :white_check_mark: \nFecha: ${fecha}"
            }
        }
        failure {
            script {
                def fecha = new Date().format('yyyy-MM-dd HH:mm:ss')
                slackSend channel: '#notificaciones-dev', message: "*${env.PROJECT_NAME}* - Fallo :x: \nFecha: ${fecha}"
            }
        }
    }
}