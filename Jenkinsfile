pipeline {
    agent any
    stages {
        stage('BuildVue') {
            steps {
                  sh 'cd dashboard & npm i'
            }
        }
        
        stage('API') {
            steps {
                  sh 'cd api & npm i'
            }
        }
        
        stage('analysis') {
            steps {
                withSonarQubeEnv('DevOpsSonarQube') {
                    withMaven(maven:'maven3'){
                        sh 'mvn sonar:sonar'
                    }
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
