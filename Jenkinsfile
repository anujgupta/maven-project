pipeline {
agent any 

stages {

  
  stage ('Github Checkout'){
    steps {
      sh "echo ${params.branch}"
      checkout([$class: 'GitSCM', branches: [[name: "*/${params.branch}"]], doGenerateSubmoduleConfigurations: false, extensions: [[$class: 'CloneOption', timeout: 120]], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'c4e0b791-0d4a-4c02-a448-23eb90b1f439', url: 'https://git.homecredit.net/country/in/welcome-mailer.git']]])
    }}
  
  stage ('Build With Maven'){
                  steps {
                         sh label: '', script: 'mvn clean install -Dspring.profiles.active=uat' 
                  }
                  
  }}}
