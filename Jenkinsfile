pipeline {
  agent any
  stages {
    stage('Pulling GitHub code to Jenkins') {
      steps {
        checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/Mija9961/Docker']]])
      }
    }
    stage('Build docker image') {
        steps {
            script{
                sh 'docker build -t mija2022/demo:v1 .'
            }
        }
    }
    stage('Push docker image to dockerhub') {
        steps {
            withCredentials([string(credentialsId: 'password_docker', variable: 'docker_passwd')]) {
                sh 'docker login -u mija2022 -p ${docker_passwd}'
                sh 'docker push mija2022/demo:v1'
            }
        }
    }
    stage('Run the image') {
        steps {
            script{
              sh 'docker run mija2022/demo:test'
            }
        }
    }
  }
}