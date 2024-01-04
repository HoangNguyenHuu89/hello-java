pipeline {

    agent any

    stages {
        stage('clean') {
            steps {
                sh "chmod +x mvnw"
                sh "./mvnw clean"
            }
        }

        stage('build application') {
            steps {
                sh "./mvnw verify -Pprod -DskipTests"
                archiveArtifacts artifacts: '**/target/*.jar', fingerprint: true
            }
        }
    }
}