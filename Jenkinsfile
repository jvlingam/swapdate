node{
    stage('SCM Checkout'){
        git 'https://github.com/jvlingam/swapdate.git'
    }
  
    stage('SonarQube analysis') {
        def scannerHome = tool 'Sonar-7.1';
        withSonarQubeEnv('sonar-7.1') {
            bat "${scannerHome}/bin/sonar-scanner.bat -Dsonar.projectKey=swapdate -Dsonar.sources=. -Dsonar.host.url=http://localhost:9000 -Dsonar.login=5271e396040d31c1c91a8606b01b2b437c2d2051"
        }
    }
    
    stage("Sonar Quality Gate check"){
          timeout(time: 1, unit: 'HOURS') {
              def qg = waitForQualityGate()
              if (qg.status != 'OK') {
                  slackSend baseUrl: 'https://hooks.slack.com/services/', 
                    channel: 'jenkins-test', 
                    color: 'danger', 
                    message: 'Sonar Quality Check failed!', 
                    teamDomain: 'NEC', 
                    tokenCredentialId: 'Slack-token'
                  error "Pipeline aborted due to quality gate failure: ${qg.status}"
              }
          }
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
