pipeline {
  agent any

  stages {
    stage('Copy artifact') {
      steps {
        copyArtifacts filter: 'sample', fingerprintArtifacts: true, projectName: 'sample', selector: workspace()
      }
    }
    stage('Deliver') {
      steps {
        sh 'scp ./sample vagrant@10.10.50.3:'
      }
    }

  }
}
