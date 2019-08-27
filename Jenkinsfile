node{
   
   stage("App Build started"){
      echo 'App build started..'
      git credentialsId: 'Github-ID', url: 'https://github.com/devopsitrain/python-docker-app-openshifts.git'
      }
   
   stage('Docker Build') {
     def app = docker.build "pythonapp"
    }
   
   stage("Tag & Push image"){
      withDockerRegistry([credentialsId: 'dockerID',url: ""]) {
          sh 'docker tag pythonapp ashithadocker/pythonapp:dev'
          sh 'docker push ashithadocker/pythonapp:dev'
      }
    }
    stage("App deployment started"){
     sh 'oc login https://api.pro-us-east-1.openshift.com --token=LwWrPErr2xFVP7PJiFG2bR9E37as-Yhpeu3sDdcalYw --server=https://api.us-east-1.online-starter.openshift.com:6443'
    // sh 'oc new-project creativetech'
      
     sh 'oc new-app ashithadocker/pythonapp:dev --name python'
     sh 'oc expose svc python --name=python'
     sh 'oc status'
    }
   
    stage('App deployed to Openshift environment') {
     echo 'App deployed to Openshift environment..'
    }

   


   
























}
