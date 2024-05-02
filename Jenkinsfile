pipeline {
	agent any 
	
	parameters {
  		string defaultValue: 'DEV', name: 'ENV'
	}
	
	triggers {
  		pollSCM '* * * * *'
	}
	
	stages {
	    stage('Checkout') {
	        steps {
			checkout scm			       
		      }}
		stage('Build') {
	           steps {
			  sh '/home/aditya/Documents/apache-maven-3.9.6/bin/mvn install'
	                 }}
		stage('Deployment'){
		    steps {
			script {
			 if ( env.ENV == 'QA' ){
        	sh 'cp target/PIPELINE-1.war /home/aditya/Documents/apache-tomcat-9.0.88/webapps'
        	echo "deployment has been COMPLETED on QA!"
			 }
			else ( env.ENV == 'UAT' ){
    		sh 'cp target/PIPELINE-1.war /home/aditya/Documents/apache-tomcat-9.0.88/webapps'
    		echo "deployment has been done on UAT!"
			}
			}}}	
}}
