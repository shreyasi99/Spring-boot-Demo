pipeline {
    agent any
tools {
  jdk 'java'
}
stages {
    stage('Cloning Git') {
            steps {
               checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'githubpassword', url: 'https://github.com/shreyasi99/Spring-boot-Demo.git']]])
            }
        }
stage("Build maven jar") {
            steps {
            sh "mvn clean package"
            }
        }
    stage("Build docker image") {
            steps {
            sh '''
            docker build -t shreya:v1 .
            docker image
            '''
            }
        }
    
    }
}
