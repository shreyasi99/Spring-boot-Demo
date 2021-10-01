pipeline {
    agent any
   tools {
  maven 'maven'
}

 stages {
    stage('Build') {
   steps {
       echo 'Hello world'
 checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'githubpassword', url: 'https://github.com/shreyasi99/Spring-boot-Demo.git']]])
 sh "mvn -Dmaven.test.failure.ignore=true clean package" }
        }
 }
}
}
