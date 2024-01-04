pipeline {

    agent any

    stages {
        stage('clone') {
            steps {
               git branch: 'main', url: 'https://github.com/HoangNguyenHuu89/hello-java.git'
            }
        }

        stage('build docker') {
            steps {
               withDockerRegistry(credentialsId: 'docker-test', url: 'https://index.docker.io/v1/') {
                   sh 'docker build -t hoangnh8997/test-docker .'
                   sh 'docker push  hoangnh8997/test-docker .'
               }
            }
        }
    }
}