node{
  stage('SCM Checkout'){
    git 'https://github.com/jvlingam/swapdate.git'
  }
  
  stage('Sonar Analysis'){
    C:\\sonarqube\\sonar-scanner\\bin\\sonar-scanner.bat -Dsonar.projectKey=swapdate -Dsonar.sources=. -Dsonar.host.url=http://localhost:9000 -Dsonar.login=5271e396040d31c1c91a8606b01b2b437c2d2051
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
