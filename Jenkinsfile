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
               dir('/var/jenkins_home/workspace/docker2'){
                  sh 'docker build -t prueba .' 
               }
            }
        }

    }
}