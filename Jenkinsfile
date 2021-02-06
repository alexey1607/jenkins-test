pipeline {
  // environment {
  //   imagename = "yenigul/hacicenkins"
  //   registryCredential = 'yenigul-dockerhub'
  //   dockerImage = ''
  // }
  agent any
  stages {
    stage('Cloning Git') {
      steps {
        git([url: 'https://github.com/alexey1607/jenkins-test.git', branch: 'master'])

      }
    }
    stage('Building image') {
      steps{
        script {
          dockerImage = docker.build imagename
        }
      }
    }

    stage('Remove Unused docker image') {
      steps{
        sh "docker rmi $imagename:$BUILD_NUMBER"
         sh "docker rmi $imagename:latest"

      }
    }
  }
}