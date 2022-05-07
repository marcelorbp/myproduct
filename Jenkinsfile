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
        stage('Compile') {
            steps {
                sh 'mvn clean compile'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
                archiveArtifacts 'target/*.xml'
            }
        }
        stage('Package') {
            steps {
                sh 'mvn package'
                archiveArtifacts 'target/*.jar'
            }
         }
        stage('Deploy') {
            steps {
                echo 'Deploy somewhere!'
            }
        }
    }
}
