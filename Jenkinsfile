pipeline {
    agent any 

    environment {
        IMAGE_TAG="0.${BUILD_ID}"
    }

    stages {
        stage('Build') {
            steps {
                sh "docker build -t simple-python-flask:${IMAGE_TAG} ."
            }
        }
        stage ('Teste'){
            steps {
                sh "docker run -tdi --name simple-python-flask-${IMAGE_TAG} --rm simple-python-flask:${IMAGE_TAG}"
                sh "docker exec simple-python-flask-${IMAGE_TAG} nosetests --with-xunit --with-coverage --cover-package=project test_users.py"
            }
        }
    }
    post {
        success {
            echo "Pipeline executada com Exito"
        }
        failure {
            echo " Pipeline falhou !!!"
        }
        cleanup {
            sh "docker stop simple-python-flask-${IMAGE_TAG}"
        }
    }
}
