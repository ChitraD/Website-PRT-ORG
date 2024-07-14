
#!groovy

pipeline {
  agent none
  stages {
    stage("Docker Build") {
      agent any
      steps {
        sh "docker build -t chitrad/website-prt-org ."
      }
    }
    stage("Docker Push") {
      agent any
      steps {
        withCredentials([usernamePassword(credentialsId: "dockerHub", passwordVariable: "dockerHubPassword", usernameVariable: "dockerHubUser")]) {
          sh "docker login -u ${env.dockerHubUser} -p ${env.dockerHubPassword}"
          sh "docker push chitrad/website-prt-org:latest"
        }
      }
    }
  }
}
