pipeline {
  agent any
  stages {
    stage('git pull') {
      steps {
        // https://github.com/Macer-Park/Gitops will replace by sed command before RUN
        git url: 'https://github.com/Macer-Park/Gitops', branch: 'main'
      }
    }
    stage('k8s deploy'){
      steps {
        kubernetesDeploy(kubeconfigId: 'kubeconfig',
                         configs: '*.yaml')
      }
    }    
  }
}