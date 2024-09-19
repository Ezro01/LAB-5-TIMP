node ('agent1') {
  def app
  stage('Cloning Git') {
    checkout scm
  }
  satge('Build-and-Tag') {
    app = docker.build("ezro01/lab-5-timp")
  }
  stage('Post-to-dockerhub') {
    docker.withRegistry('https://registry.hub.docker.com', 'dockerhub_creds') {
      app.push("latest")
    }
  }
  stage('Pull-image-server') {
  sh "docker-compose down"
  sh "docker-compose up-d"
  }
}
