@Library('piper-lib-os') _

node() {
  stage('init') {
    deleteDir()
    checkout scm
  }

  stage('Build and test')   {
      mtaBuild script:this
  }

  stage('Deploy')   {
      cloudFoundryDeploy script:this, deployTool:'mtaDeployPlugin'
  }
}
