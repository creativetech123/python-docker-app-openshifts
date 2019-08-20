node{
   
   stage("App Build started"){
      echo 'App build started..'
      git credentialsId: 'githubID', url: 'https://github.com/creativetech123/python-docker-app-openshifts.git'     
   }
   
   stage('Docker Build') {
     def app = docker.build "siddukuri/dockerrepo"
    }
   
   stage("Tag & Push image"){
      withDockerRegistry(credentialsId: 'docker-ID', url: 'https://hub.docker.com/?namespace=siddukuri') {
          sh 'docker tag siddukuri/dockerrepo siddukuri/dockerrepo:dev'
          sh 'docker push siddukuri/dockerrepo:dev'
          sh 'docker push siddukuri/dockerrepo:latest'
      }
    }
   
   stage("App deployment started"){
     
    }
   
    stage('App deployed to Openshift environment') {
     echo 'App deployed to Openshift environment..'
    }

   
























}
