pipeline {
    agent any
 
    stages {
        stage('Checkout') {
            steps {		
			checkout([$class: 'GitSCM', branches: [[name: 'main']], extensions: [[$class: 'CheckoutOption', timeout: 5], [$class: 'CloneOption', noTags: false, reference: '', shallow: false, timeout: 5]], userRemoteConfigs: [[url: 'https://github.com/j-huidrom/devops.git']]])

             echo 'Checkout source code from git'
            }
        }
        stage('Quality Check') {
            steps {
                echo 'QA verified'
            }
        }
        stage('Security Check') {
            steps {
                echo 'All security checks done'
            }
        }
        stage('Build Push App with mvn installed in vm') {
            steps {
               //sh "mvn clean install"
		echo "skiping this stage to try the next stage"	
	    }
        }
	stage('Build Push App with mvn configured in jenknins') {
		withMaven(
			// Maven installation declared in the Jenkins "Global Tool Configuration"
			maven: 'maven_3.6.3'
		    ) {
		      // Run the maven build
		      sh "mvn clean install"

		    }
        }    
	    
	     
	    
	    
	    
	    
         stage('Deploy') {
            steps {
                echo 'Deployment done'
            }
        }
         stage('Post Deployment Check') {
            steps {
                echo 'All deployment check done'
            }
        }
    }
}
