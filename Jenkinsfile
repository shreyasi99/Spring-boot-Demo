pipeline {
    agent any
    tools {
        maven "3.6.0" // You need to add a maven with name "3.6.0" in the Global Tools Configuration page
    }
 stages {
    stage('Cloning Git') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/shreyasi99/Spring-boot-Demo.git']]])
            }
        }
         // here we build the maven project and generated jar file , with the help of this file generated docker image
    stage('Build jar file') { 
           steps {
              withMaven(maven: 'maven3'){dir ('spring-boot-maven-example-helloworld'){ sh 'mvn -B -DskipTests clean package' }}
            } 
         }
    // Building Docker images
     stage('build') {
            steps {
                echo "Hello World!"
        }
      }
     }
}
