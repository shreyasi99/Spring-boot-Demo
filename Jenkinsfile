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
stage("Build") {
            steps {
            sh "mvn clean package"
            }
        }
    }
}
