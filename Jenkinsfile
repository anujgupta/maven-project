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
      checkout([$class: 'GitSCM', branches: [[name: 'master']], doGenerateSubmoduleConfigurations: false, extensions: [[$class: 'CloneOption', timeout: 120]], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'c4e0b791-0d4a-4c02-a448-23eb90b1f439', url: 'https://git.homecredit.net/country/in/m-site.git']]])
    }}
  
  
  stage ('Build With NG'){
                  steps {
                         sh label: '', script: "ng build --prod"
                  }
                  
  }

stage ('Deploy on DeployServer') {
                        steps  {			  
				sh label: '', script: "scp ${WORKSPACE}/target/dist sinvx064.in.nonprod:/tmp"			  
			  }
			  
		}}}
