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
          sh 'docker tag py-app shiddu/py-app:lts'
          
          sh 'docker push shiddu/py-app:lts'
          
      }
    }
   
   stage("App deployment started"){
     sh 'oc login --token=CQfvSffhwy7g0b2xZFdd-oV_oG_y-3Jh2o8iEx34BVo --server=https://api.us-east-1.online-starter.openshift.com:6443'
    // sh 'oc new-project creativetech'
      
     sh 'oc new-app shiddu/py-app:lts --name python-app' 
      //'--env NEW_RELIC_LICENSE_KEY=a0360aa08a234e979d6bd9f8feec22aa3684f8e4 NEW_RELIC_APP_NAME=py-app' 
     sh 'oc expose svc python-app --name=python-app'
     
     sh 'oc status'
    }
   
    stage('App deployed to Openshift environment') {
     echo 'App deployed to Openshift environment..'
    }

}
