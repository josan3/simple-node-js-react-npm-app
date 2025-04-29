pipeline {
    agent {
        docker {
            image 'node:20.10.0-alpine3.18'  // Imagen de Docker
            args '-p 3000:3000'  // Puertos
        }
    }

    stages {
        stage('Build') {
            steps {
                // Instalar dependencias
                sh 'npm install'
            }
        }

        stage('Deliver') {
            steps {
                // Ejecutar el script de entrega
                sh './jenkins/scripts/deliver.sh'
                
                // Solicitar entrada del usuario
                input message: 'Finished using the website? (Click "Proceed" to continue)'
                
                // Ejecutar el script para matar procesos
                sh './jenkins/scripts/kill.sh'
            }
        }
    }
}
