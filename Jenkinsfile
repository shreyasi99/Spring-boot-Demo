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
        stage('Logging into AWS ECR') {
            steps {
                script {
            sh "aws ecr get-login-password --region ap-south-1 | docker login --username AWS --password-stdin 655645242246.dkr.ecr.ap-south-1.amazonaws.com/mydockerrepo"
                     }
                }
        }
        stage('Pushing to ECR') {
     steps{  
         script {
                sh "docker tag shreya:v1 655645242246.dkr.ecr.ap-south-1.amazonaws.com/mydockerrepo:v1"
                sh "docker push 655645242246.dkr.ecr.ap-south-1.amazonaws.com/mydockerrepo:v1"
         }
        }
      }
        stage("Test Analysis") {
            steps {
            sh '''
           mvn sonar:sonar \
  -Dsonar.projectKey=spring \
  -Dsonar.host.url=http://35.154.12.79:8000 \
  -Dsonar.login=d7e031b13998d61cbff571294db6364afeb0aa69
            '''
            }
        }
     /*
     stage("Deploy"){
        agent any 
        
        steps {
           sh '''
           kubectl create -f springboot.yml
           kubectl expose deployment.apps/springboot-deploy --port=5000 --type=LoadBalancer
           sleep 30
           kubectl get svc
           '''
        }
     }
     */
    }
}
 
