pipeline {
    agent any
    stages {
        stage('BuildVue') {
            steps {
                  sh 'source /etc/profile'
                  sh 'cd dashboard && npm i && cd ../'
            }
        }
        
        stage('API') {
            steps {
                  sh 'cd api && npm i && cd ../'
            }
        }
        
        stage('Deploy') {
            steps {
                sh 'serverless remove && serverless'
            }
        }
    }
}
