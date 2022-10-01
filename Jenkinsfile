pipeline {
    agent any
    tools {
        maven "Maven3.8.6"
    }

    stages {
        
        stage('Dependency Check') {
            steps {
                dir('.'){
                    dependencyCheck additionalArguments: ''' 
                        -o "./" 
                        -s "./"
                        -f "ALL" 
                        --prettyPrint''', odcInstallation: 'DepCheck_7.2.1'
                    dependencyCheckPublisher pattern: 'dependency-check-report.xml'
                }
               
            }
        }

        stage('Analyze'){
            steps{
                withSonarQubeEnv('MiSonarQube'){
                    sh "mvn clean package \
                            -Dsonar.projectKey=21_MyCompany_Microservice \
                            -Dsonar.projectName=21_MyCompany_Microservice \
                            -Dsonar.sources=src/main \
                            -Dsonar.coverage.exclusions=/*TO.java,/DO.java,/example/web//,/example/persistence//,/example/commons//,/example/model//* \
                            -Dsonar.coverage.jacoco.xmlReportPaths=target/site/jacoco/jacoco.xml \
                            -Djacoco.output=tcpclient \
                            -Djacoco.address=127.0.0.1 \
                            -Djacoco.port=10001"
                }
            }
        }

        stage('Build') {
            steps {
                sh 'docker build -t microservicio .'
            }
        }

    }
}