pipeline {
    agent any

    stages {
        stage('Build Docker Image') {
            steps {
                sh 'docker build --no-cache -t ci-cd-jenkins .'
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                  docker rm -f ci-cd-jenkins || true
                  docker run -d -p 8081:80 --name ci-cd-jenkins ci-cd-jenkins
                '''
            }
        }
    }
}
