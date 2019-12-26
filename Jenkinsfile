pipeline {
agent any 

stages {

  stage('echo') {
           steps {
               
                sh "echo ${env.WORKSPACE}"
            }
        }
  
  stage ('Github Checkout'){
    steps {
      sh "echo ${params.branch}"
      checkout([$class: 'GitSCM', branches: [[name: 'hcin-octopus-release']], doGenerateSubmoduleConfigurations: false, extensions: [[$class: 'CloneOption', timeout: 120]], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'c4e0b791-0d4a-4c02-a448-23eb90b1f439', url: 'https://git.homecredit.net/country/in/octopus.git']]])
    }}
  
  
  stage ('Maven Build'){
                  steps {
                         sh label: '', script: " mvn clean install -P test"
                  }
                  
  }

stage ('Deploy on DeployServer') {
                        steps  {			  
				sh label: '', script: "scp ${WORKSPACE}/target/*.war sinvx063.test.homecredit.in:/tmp"			  
			  }
			  
		}}}
