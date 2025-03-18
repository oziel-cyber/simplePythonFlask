pipeline {
    agent any 

    environment {
        IMAGE-TAG="0.${BUILD_ID}"
    }

    stages {
        stage('Build') {
            steps {
                sh "docker build -t simple-python-flask ."
            }
        }
        stage ('Teste')
            steps {

            }
    }
}
