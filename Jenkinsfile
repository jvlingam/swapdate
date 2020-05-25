node{
  stage('SCM Checkout'){
    git 'https://github.com/jvlingam/swapdate.git'
  }
  
  stage('Email Notification'){
    mail bcc: '', body: 'Hi, It is Vijay here...', cc: '', from: '', replyTo: '', subject: 'Test mail from Jenkins', to: 'vijay.yajiv.j@gmail.com'
  }
  
  stage('slack Notification'){
    slackSend baseUrl: 'https://hooks.slack.com/services/', 
      channel: 'jenkins-test', 
      color: 'good', 
      message: 'Welcome to slack, jenkins!', 
      teamDomain: 'NEC', 
      tokenCredentialId: 'Slack-token'
  }
}
