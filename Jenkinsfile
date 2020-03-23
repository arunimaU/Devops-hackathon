pipeline {
   agent any
	stages {
      stage('Git Checkout') {
         steps {
           checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/arunimaU/Devops-hackathon.git']]])
		}
	}
	stage ('Build')
	   
	    {steps{
                sh '/opt/maven/bin/mvn clean package -Dmaven.test.skip=true'
	    }    }
		stage ('release')
		{steps{
	        sh '/opt/maven/bin/mvn --batch-mode release:clean release:prepare release:perform -DreleaseVersion-1.0 -DmasterVersion-1.0-SNAPSHOT'
	        sh 'sudo git add .'
                sh 'sudo git commit -m "Updated pom" pom.xml'
                sh 'sudo git push https://arunimaU:arunimaU@github.com/arunimaU/Devops-hackathon.git HEAD:master'
                }       }
      }
          
   }
