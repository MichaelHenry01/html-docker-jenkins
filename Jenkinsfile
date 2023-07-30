pipeline {
    agent any
    
    stages {
        stage('grab-code') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], userRemoteConfigs: [[url: 'https://github.com/Mostafa-Anwar/simple-html-app.git']]])
            }
        }
        
        stage('build-image') {
            steps {
                sh "docker build -t jenkins-demo:${BUILD_NUMBER} ."
            }
        }

        stage('tag-image') {
            steps {
                sh "docker tag jenkins-demo:${BUILD_NUMBER} jenkins-demo:latest"
            }
        }
    }
}
