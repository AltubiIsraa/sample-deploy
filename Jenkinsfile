pipeline {
  agent any
  
  parameters {
  choice choices: ['qa', 'production'], description: 'Select environment for deployment', name: 'DEPLOY_TO'
}


  stages {
    stage('Copy artifact') {
      steps {
        copyArtifacts filter: 'sample', fingerprintArtifacts: true, projectName: 'sample-multibranch/umaima', selector: lastSuccessful()
      }
    }
    stage('Deliver') {
      steps {
          sshagent(['vagrant-private-key']) {
          sh 'ANSIBLE_HOST_KEY_CHECKING=False ansible-playbook -i ${DEPLOY_TO}.ini playbook.yml'
        }
      }
    }

  }
}
