pipeline {
    agent any

    stages {
        stage('Borrado previo') {
            steps {
               dir('/var/jenkins_home/workspace/docker2'){
                  sh 'docker build -t prueba .' 
               }
            }
        }

    }
}