pipeline {
    agent any
    stages {
        stage('BuildVue') {
            steps {
                  sh 'cd dashboard && npm i && cd ../'
            }
        }
        
        stage('BuildAPI') {
            steps {
                  sh 'cd api && npm i && cd ../'
            }
        }
        
        stage('Analysis') {
            steps {
                withSonarQubeEnv('DevOpsSonarQube') {
                        sh 'sonar-scanner'
                }
            }
        }
        
        stage('Deploy') {
            steps {
                sh 'serverless remove && serverless'
            }
        }
    }
}
