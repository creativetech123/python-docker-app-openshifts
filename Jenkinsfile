node{
   
   stage("App Build started"){
      echo 'App build started..'
      git credentialsId: 'githubID', url: 'https://github.com/creativetech123/python-docker-app-openshifts.git'     
   }
   
   stage('Docker Build') {
     def app = docker.build "pythonimage"
    }
   
   stage("Tag & Push image"){
      withDockerRegistry(credentialsId: 'docker-ID', url: '') {
          sh 'docker tag pythonimage shiddu/pythonimage:dev'
          
          sh 'docker push shiddu/pythonimage:dev'
          
      }
    }
   
   stage("App deployment started"){
     sh 'oc login --token=t01XSPheqChA1n1QxmPCSJAwm5rFNYzb7FvRP9mmg6A --server=https://api.us-east-1.online-starter.openshift.com:6443'
    // sh 'oc new-project creativetech'
      
     sh 'oc new-app shiddu/pythonimage:dev --name python'
     sh 'oc expose svc python --name=python'
     sh 'oc status'
    }
   
    stage('App deployed to Openshift environment') {
     echo 'App deployed to Openshift environment..'
    }

   
























}
