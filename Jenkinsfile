node{
   
   stage("App Build started"){
      echo 'App build started..'
      git credentialsId: 'githubID', url: 'https://github.com/creativetech123/python-docker-app-openshifts.git'     
   }
   
   stage('Docker Build') {
     def app = docker.build "py-app"
    }
   
   stage("Tag & Push image"){
      withDockerRegistry(credentialsId: 'docker-ID', url: '') {
          sh 'docker tag py-app shiddu/pythonimage-app:lts'
          
          sh 'docker push shiddu/py-app:lts'
          
      }
    }
   
   stage("App deployment started"){
     sh 'oc login --token=ZmGj7NzELrDmUgDoCmkA3QbYXimFkmmuVgYWKPb34Qs --server=https://api.us-east-1.online-starter.openshift.com:6443'
    // sh 'oc new-project creativetech'
      
     sh 'oc new-app shiddu/py-app:lts --name py-app'
     sh 'oc expose svc py-app --name=py-app'
     sh 'oc status'
    }
   
    stage('App deployed to Openshift environment') {
     echo 'App deployed to Openshift environment..'
    }

   
























}
