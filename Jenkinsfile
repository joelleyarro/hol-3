pipeline {
    agent any
    tools {
        maven 'M2_HOME'
    }
    stages {
         stage('build') {
            steps {
                echo 'Hello build'
                sh 'mvn clean'
                sh 'mvn install'
                sh 'mvn package'
            }
        }
    stage('test') {
            steps {
                echo 'mvn test'
            }
        }
    stage('build and publish image') {
            steps {
              script {
                 checkout scm
                 docker. withResgistery('', 'DockerRgisteryID') {
                 def customImage = docker.docker.build("joelleyarro/holliday-pipeline:${env.BUILD_ID}")
                 customImage.push()  
                     }
                 }
            }
        } 
    }       
}
   
