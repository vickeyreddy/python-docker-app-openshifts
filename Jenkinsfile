node{
   
   stage("App Build started"){
      echo 'App build started..'
      git credentialsId: 'Github-ID', url: 'https://github.com/vickeyreddy/python-docker-app-openshifts.git'
      }
   
   stage('Docker Build') {
     def app = docker.build "vickeyreddy/python-docker-app"
    }
   
   stage("Tag & Push image"){
      withDockerRegistry([credentialsId: 'Github-ID', url: 'https://index.docker.io/v1/']) {
          sh 'docker tag vickeyreddy/python-docker vickeyreddy/python-docker'
          sh 'docker push vickeyreddy/python-docker:001'
          sh 'docker push vickeyreddy/python-docker:latest'
      }
    }
   
   stage("App deployment started"){
     sh 'oc login https://api.starter-us-west-1.openshift.com --token=l334xAzzGBl7kvYuUFcvfRCCXMsQxeQJox3pEzbSQrQ'
     sh 'oc new project python-docker'
     sh 'oc new-app vickeyreddy/python-docker --name python-app'
     sh 'oc expose svc python-app --name=python-app'
     sh 'oc status'
    }
   
    stage('App deployed to Openshift environment') {
     echo 'App deployed to Openshift environment..'
    }

   
























}
