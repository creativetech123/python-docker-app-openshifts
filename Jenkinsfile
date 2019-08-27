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
          sh 'docker tag pythonimage shiddu/pythonimage:lts'
          
          sh 'docker push shiddu/pythonimage:lts'
          
      }
    }
   
   stage("App deployment started"){
     sh 'oc login --token=Y6jJPO7MVmWYMKbtrDmYBOTNDivOe7Vch7F1hdE1w6k --server=https://api.us-east-1.online-starter.openshift.com:6443'
    // sh 'oc new-project creativetech'
      
     sh 'oc new-app shiddu/pythonimage:lts --name python-application'
     sh 'oc expose svc python-application --name=python-application'
     sh 'oc status'
    }
   
    stage('App deployed to Openshift environment') {
     echo 'App deployed to Openshift environment..'
    }

   
























}
