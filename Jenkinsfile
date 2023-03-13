pipeline {
  agent any

  stages {
    stage('Build image') {
      steps {
        script {
          docker.build("amazonlinux-2023:${env.BUILD_NUMBER}")
        }
      }
    }

    stage('Tag image') {
      steps {
        script {
            sh 'curl -fsSL https://get.docker.com -o get-docker.sh && sh get-docker.sh'
          docker.withRegistry("yiidp.jfrog.io/docker-image-level0", "cmVmdGtuOjAxOjE3MTAyMDg5NjU6bjNwWFFYd3VRSUpZVGdFRU5RRUNGeFRnYTND") {
            docker.image("amazonlinux-2023:${env.BUILD_NUMBER}").push("latest")
          }
        }
      }
    }
  }
}
