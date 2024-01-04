#!/usr/bin/env groovy
pipeline {

    agent any

    tools {
        jdk 'openjdk-21.0.1'
    }

    stages {

        stage('check env') {
            steps {
                sh "java -version"
                sh "docker -v"
                sh "helm version"
            }
        }

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