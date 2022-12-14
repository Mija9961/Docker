pipeline {
  agent any
  stages {
    stage('Pulling GitHub code to Jenkins') {
      steps {
        checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/Mija9961/Docker']]])
      }
    }
  }
}