#!/usr/bin/env groovy
pipeline {
    agent any

    tools {
         maven 'MAVEN'
    }

    stages{
        stage('Checkout') {
            steps{
                 git changelog: false, poll: false, url: 'https://github.com/marcelorbp/myproduct.git'
            }
        }
        stage('Build') {
            steps {
                sh 'mvn clean compile'
              //  archiveArtifacts artifacts: '**/target/*.jar', fingerprint: true
            }
        }
        stage('Test') {
            steps {
                /* `make check` returns non-zero on test failures,
                * using `true` to allow the Pipeline to continue nonetheless
                */
          //      sh 'make check || true'
          //      junit '**/target/*.xml'
                sh 'mvn test'

            }
        }
        stage('Deploy') {
            steps {
                sh 'mvn deploy'
            }
        }
    }
}
