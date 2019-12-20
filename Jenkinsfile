pipeline {
agent any 

stages {

  stage('echo') {
           steps {
                // sh "echo ${params.URL}"
                //sh "echo ${params.branch}"
                //sh "echo ${params.target}"
                sh "echo ${env.WORKSPACE}"
		// sh "echo ${params.deployserver}"
            }
        }
  
  stage ('Github Checkout'){
    steps {
      sh "echo ${params.branch}"
      checkout([$class: 'GitSCM', branches: [[name: 'hcin-imps-dev']], doGenerateSubmoduleConfigurations: false, extensions: [[$class: 'CloneOption', timeout: 120]], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'c4e0b791-0d4a-4c02-a448-23eb90b1f439', url: 'https://git.homecredit.net/country/in/citi-imps.git']]])
    }}
  
  
  stage ('Build With Maven'){
                  steps {
                         sh label: '', script: "mvn clean install"
                  }
                  
  }

stage ('Deploy on DeployServer') {
                        steps  {			  
				sh label: '', script: "scp ${WORKSPACE}/target/*.war upinp01-dmzin1cus.in.prod:/tmp"			  
			  }
			  
		}}}
