env.environment =""
env.browserName= "firefox"

pipeline {
agent any 

stages {
        stage('Checkout Code..') {
		when {
                   anyOf { 
		   branch 'master'; branch 'stg' ; 
		   }
	           beforeAgent true
		   }
                   steps {
		   echo 'Hello World'
                   script {			    	
                   if ("${env.GIT_BRANCH}" == "master") {
                   env.environment = "dev"
		    } else if("${env.GIT_BRANCH}" == "STG"){
                   env.environment = "stg"
		    } else {
                    env.environment = "false"
                   }
		    echo env.environment
		    checkout([$class: 'GitSCM', branches: [[name: 'master']],doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/agupta89/TestDev.git']]])
                    
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
