env.environment =""
properties([pipelineTriggers([githubPush()])])


pipeline {
agent any 

stages {
        stage('Checkout Code..') {
		when {
                   anyOf { 
		   branch 'master'; branch 'STG' ; 
		   }
	           beforeAgent true
		   }
                   steps {
		   echo 'Hello World'
			    echo env.GIT_BRANCH
			   
                   script {	
			   env.branch = "${env.GIT_BRANCH}"
                   if ("${env.GIT_BRANCH}" == "master") {
                   env.environment = "dev"
		    } else if("${env.GIT_BRANCH}" == "STG"){
                   env.environment = "stg"
		    } else {
                    env.environment = "false"
                   }
		    echo env.environment
		    checkout([$class: 'GitSCM', branches: [[name: env.branch]],doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/agupta89/TestDev.git']]])
                    
                }
		  		
            }
}

    stage('Checkout Testing Code') {
           steps {     
          echo env.environment
        }
    }

      stage('Publish Html Report') {
            steps {
                echo 'Extend Report'       
        }

        }   
}
}
