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
     sh 'oc login --token=nYolyX-cqohjHOU4vjJiwNo18YOgemhRldkzBRoXY-E --server=https://api.us-east-2.online-starter.openshift.com:6443'
     //sh 'oc new project python-docker'
     sh 'oc  import-image vickeyreddy/python-docker:pattabhi-1.0 --name python-app2'
     sh 'oc expose svc python-app2 --name=python-app2'
     sh 'oc status'
    }
   
    stage('App deployed to Openshift environment') {
     echo 'App deployed to Openshift environment..'
    }

   
























}
