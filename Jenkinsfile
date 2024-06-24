pipeline {
  agent any
  stages {
<<<<<<< HEAD
=======
    stage('Deploy start') {
      steps {
        slackSend(message: "Deploy ${env.BUILD_NUMBER} Started"
        , color: 'good', tokenCredentialId: 'slack-key')
      }
    }      
>>>>>>> f1dd8db0cccdedd55ece010f950f710ae99cd629
    stage('git pull') {
      steps {
        // https://github.com/Macer-Park/Gitops.git will replace by sed command before RUN
        git url: 'https://github.com/Macer-Park/Gitops.git', branch: 'main'
      }
    }
    stage('k8s deploy'){
      steps {
        kubernetesDeploy(kubeconfigId: 'kubeconfig',
                         configs: '*.yaml')
      }
<<<<<<< HEAD
    }    
=======
    }
    stage('send diff') {
      steps {
        script {
          def publisher = LastChanges.getLastChangesPublisher "PREVIOUS_REVISION", "SIDE", "LINE", true, true, "", "", "", "", ""
          publisher.publishLastChanges()
          def htmlDiff = publisher.getHtmlDiff()
          writeFile file: "deploy-diff-${env.BUILD_NUMBER}.html", text: htmlDiff
        }
        slackSend(message: """${env.JOB_NAME} #${env.BUILD_NUMBER} End
        (<${env.BUILD_URL}/last-changes|Check Last changed>)"""
        , color: 'good', tokenCredentialId: 'slack-key')             
      }
    }
>>>>>>> f1dd8db0cccdedd55ece010f950f710ae99cd629
  }
}