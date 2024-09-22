pipeline {
    agent any

    environment {
        GOOGLE_APPLICATION_CREDENTIALS = 'C:\\ProgramData\\Jenkins\\.jenkins\\key\\deploy-2.json' // Ruta a tu archivo JSON
    }

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/braninostroza/test.git', branch: 'main' // Reemplaza con tu repositorio
            }
        }

        stage('Install Dependencies') {
            steps {
                bat 'npm install -g yarn'
                bat 'yarn --version' // Verificar que Yarn está instalado
                bat 'yarn install'    // Instalar dependencias
            }
        }       

        stage('Build') {
            steps {
                bat 'npm run build' // Construir la aplicación
            }
        }

        stage('Deploy to Firebase') {
            steps {
                bat 'firebase deploy' // Desplegar a Firebase
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
