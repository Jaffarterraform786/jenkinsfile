pipeline{
  agent any
  environment {
  PATH = "{$path}:${getTerraformPath()}"
}

stages{
  stage('terraform init'){
    steps{
      sh 'terraform init'
      sh 'terraform apply -auto-approve'
    }
  }
  stage('jenkins build alerts'){
   steps{
  slackSend(channel: '#jenkins-deployments', color: '#009933', message: 'job1 build sucessful', teamDomain: 'jenkinsteamtalk',
  tokenCredentialId: 'slack-jenkins1')
  }
  }
  }
  }
  def getTerraformPath(){
  tfHome = tool name: 'terraform 0.15', type: 'terraform'
  return tfHome
  }
