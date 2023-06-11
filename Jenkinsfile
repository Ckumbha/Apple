pipeline {
	agent{
	label 'SLAVE-2'
	}
	parameters {
		choice(name: 'ENVIRONMENT', choices: ['QA','UAT'], description: 'Pick Environment value')
	}
	stages {
	    stage('Checkout') {
	        steps {
			checkout scm			       
		      }}
		stage('Build') {
	           steps {
			  sh '/home/chetan/SLAVE/apache-maven-3.6.3/mvn install'
	                 }}
		stage('Deployment'){
		    steps {
			sh 'sshpass -p "dev" scp target/Apple.war chetan@172.17.0.2:/home/chetan/SLAVE/apache-tomcat-9.0.75/webapps'
			}}
		stage('Docker build'){
		    steps {
			sh 'docker build -t chetankumbhare/pipelineimage11.1.2 .'
			}}
		stage('Docker Login'){
		    steps {
		withCredentials([string(credentialsId: '51e384e0-8192-4bac-a1d1-697d479a88fe', variable: 'Docker-Creds')]){
    		sh 'docker login -u chetankumbhare -p${Docker-Creds}'                 
			echo 'Login Completed'
			}
			
			}}
		stage('Push Image to Docker Hub') {         
    		    steps{                            
 			sh 'docker push chetankumbhare/pipelineimage11.1.2:$BUILD_NUMBER'           
			echo 'Push Image Completed'       
    			}}
		
}}

