pipeline {
    agent any

    environment {
        FIREBASE_TOKEN = credentials('firebase-token') // Asegúrate de tener este token en Jenkins
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/braninostroza/test.git' // Reemplaza con tu repositorio
            }
        }

        stage('Install Dependencies') {
            steps {
                script {
                    // Instalar Yarn si no está instalado
                    sh 'npm install -g yarn'
                }
                sh 'yarn install' // Instalar dependencias
            }
        }

        stage('Build') {
            steps {
                sh 'yarn build' // Construir la aplicación
            }
        }

        stage('Deploy to Firebase') {
            steps {
                sh 'firebase deploy --token $FIREBASE_TOKEN' // Desplegar a Firebase
            }
        }
    }

    post {
        success {
            echo 'Despliegue exitoso en Firebase.'
        }
        failure {
            echo 'El despliegue ha fallado.'
        }
    }
}
