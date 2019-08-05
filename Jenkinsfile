node{
   
   stage("App Build started"){
      echo 'App build started..'
      git credentialsId: 'Github-ID', url: 'https://github.com/vickeyreddy/python-docker-app-openshift'
      }
   
   stage('Docker Build') {
     def app = docker.build "vickeyreddy/python-docker-app"
    }
   
   stage("Tag & Push image"){
      withDockerRegistry([credentialsId: 'Github-ID', url: 'https://index.docker.io/v1/']) {
          sh 'docker tag vickeyreddy/python-docker-app vickeyreddy/python-docker-app'
          sh 'docker push vickeyreddy/python-docker-app:001'
          sh 'docker push vickeyreddy/python-docker-app:latest'
      }
    }
   
   stage("App deployment started"){
     sh 'oc login https://api.starter-us-west-1.openshift.com --token=l334xAzzGBl7kvYuUFcvfRCCXMsQxeQJox3pEzbSQrQ'
     sh 'oc new project python-docker-app'
     sh 'oc new-app vickeyreddy/python-docker-app:pattabhi-1.0 --name python-app'
     sh 'oc expose svc python-app --name=python-app'
     sh 'oc status'
    }
   
    stage('App deployed to Openshift environment') {
     echo 'App deployed to Openshift environment..'
    }

   
























}
