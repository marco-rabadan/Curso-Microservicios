pipeline {
    agent any

    stages {
        stage('Revision de ruta') {
            steps {
               sh 'pwd'
            }
        }
        stage('Borrado previo') {
            steps {
               sh 'docker build -t prueba .'
            }
        }

    }
}