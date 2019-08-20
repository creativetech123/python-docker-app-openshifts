node{
   
   stage("App Build started"){
      echo 'App build started..'
      git credentialsId: 'githubID', url: 'https://github.com/creativetech123/python-docker-app-openshifts.git'     
   }
   
   stage('Docker Build') {
     def app = docker.build "shiddukuri2275/creativetech123"
    }
   
   stage("Tag & Push image"){
      withDockerRegistry(credentialsId: 'docker-ID', url: 'https://hub.docker.com/?namespace=siddukuri') {
          sh 'docker tag shiddukuri2275/creativetech123 shiddukuri2275/creativetech123:dev'
          sh 'docker push shiddukuri2275/creativetech123:dev'
          sh 'docker push shiddukuri2275/creativetech123:latest'
      }
    }
   
   stage("App deployment started"){
     
    }
   
    stage('App deployed to Openshift environment') {
     echo 'App deployed to Openshift environment..'
    }

   
























}
