pipeline {
    agent any
    stages {
        stage('BuildVue') {
            steps {
                  sh 'cd dashboard && npm i && cd ../'
            }
        }
        
        stage('API') {
            steps {
                  sh 'cd api && npm i && cd ../'
            }
        }
        
        stage('analysis') {
            steps {
                withSonarQubeEnv('DevOpsSonarQube') {
                        sh '${scannerHome}/bin/sonar-scanner'
                }
            }
        }
        
        stage('Deploy') {
            steps {
                sh 'serverless remove & serverless'
            }
        }
    }
}
