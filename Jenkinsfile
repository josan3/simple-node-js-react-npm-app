pipeline {
    agent any

    stages {
        agent {
            docker {
                image 'node:20.10.0-alpine3.18' // Imagen de Docker
                args '-p 3000:3000' // Puertos
            }
        }
        stages {
            stage('Build') {
                steps {
                sh 'npm install' // Instalar dependencias
                }
            }
        
            stage('Deliver') {
                steps {
                    sh './jenkins/scripts/deliver.sh'
                    input message: 'Finished using the web site? (Click "Proceed" to continue)'
                    sh './jenkins/scripts/kill.sh'
                }
            }
        }

    }
}