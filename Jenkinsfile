pipeline {
agent any 

stages {

  
  stage ('Github Checkout'){
    steps {
      sh "echo ${params.branch}"
      checkout([$class: 'GitSCM', branches: [[name: "*/${params.branch}"]], doGenerateSubmoduleConfigurations: false, extensions: [[$class: 'CloneOption', timeout: 120]], submoduleCfg: [], userRemoteConfigs: [[credentialsId: '4241e7f8-b7a8-4d36-b055-84dc48c6da5a', url: 'https://git.homecredit.net/country/in/welcome-mailer.git']]])
    }}
  
  stage ('Build With Maven'){
                  steps {
                         sh label: '', script: 'mvn clean install -Dspring.profiles.active=uat' 
                  }
                  
              }
