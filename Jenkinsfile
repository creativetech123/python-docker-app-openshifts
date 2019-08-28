node{
   
   stage("App Build started"){
      echo 'App build started..'
      git credentialsId: 'githubID', url: 'https://github.com/creativetech123/python-docker-app-openshifts.git'     
   }
   
   stage('Docker Build') {
     def app = docker.build "pythonimage-app"
    }
   
   stage("Tag & Push image"){
      withDockerRegistry(credentialsId: 'docker-ID', url: '') {
          sh 'docker tag pythonimage-app shiddu/pythonimage-app:1.0'
          
          sh 'docker push shiddu/pythonimage-app:1.0'
          
      }
    }
   
   stage("App deployment started"){
     sh 'oc login --token=2JwqN3p3S0Q7ABqTXUi3HKXKNjE6YWNWVoJF9vZdK_A --server=https://api.us-east-1.online-starter.openshift.com:6443'
    // sh 'oc new-project creativetech'
      
     sh 'oc new-app shiddu/pythonimage-app:lts --name python-app'
     sh 'oc expose svc python-app --name=python-app'
     sh 'oc status'
    }
   
    stage('App deployed to Openshift environment') {
     echo 'App deployed to Openshift environment..'
    }

   
























}
