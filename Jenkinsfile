node{
   
   stage("App Build started"){
      echo 'App build started..'
      git credentialsId: 'githubID', url: 'https://github.com/creativetech123/python-docker-app-openshifts.git'     
   }
   
   stage('Docker Build') {
     def app = docker.build "shiddu/pythonapp"
    }
   
   stage("Tag & Push image"){
      withDockerRegistry(credentialsId: 'docker-ID', url: '')  {
          sh 'docker tag shiddu/pythonapp shiddu/pythonapp:dev'
          sh 'docker push shiddu/pythonapp:dev'
          sh 'docker push shiddu/pythonapp:latest'
      }
    }
   
   stage("App deployment started"){
     
    }
   
    stage('App deployed to Openshift environment') {
     echo 'App deployed to Openshift environment..'
    }

   
























}
