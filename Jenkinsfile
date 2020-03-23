pipeline {
   agent any
	stages {
      stage('Git Checkout') {
         steps {
            checkout([$class: 'GitSCM', branches: [[name: '*/release']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/arunimaU/Devops-hackathon.git']]])
		}
	}
	stage ('Build')
	   
	    {steps{
                sh '/usr/share/maven/bin/mvn clean package -Dmaven.test.skip=true'
	    }    }
       stage ('Update the Version')
		{ steps {
                sh '/usr/share/maven/bin/mvn --batch-mode release:clean release:prepare release:perform -DreleaseVersion-5.1.1 -DdevelopmentVersion-1.6.2-SNAPSHOT -Dmaven.test.skip=true'
	        sh 'sudo git add .'
                sh 'sudo git commit -m "Updated pom" pom.xml'
                sh 'sudo git push https://arunimaU:arunimaU@github.com/arunimaU/Devops-hackathon.git HEAD:release'
                }       }
            
	}
        
}
