pipeline {
  agent none
  
  environment {
    REGISTRY_URL = '3.35.252.125:8000'
    REGISTRY_CREDENTIALS = 'harbor-docker-registry'
    APP_IMAGE = null
    IMAGE_REPO = 'petclinic'
    IMAGE_NAME = 'spring-petclinic-angular'
    //IMAGE_TAG = sh(returnStdout: true, script: '(git rev-parse --short HEAD && echo "_$BUILD_NUMBER") | tr -d "\n"').trim()
    IMAGE_TAG = '4ab59b2_17'
  }

  stages {

    stage( 'Deploy to Cluster' ) {
      steps {
        script {
          kubernetesDeploy(kubeconfigId: 'kubeconfig-sa-token', configs: 'spring-petclinic-angular2.yaml')
        }
        sh 'sleep 20'
      }
    }
    
  }
}
