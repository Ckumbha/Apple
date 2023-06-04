pipeline {
	agent any 
	stages {
		stage('Checkout'){
		  steps {
			checkout scm 
			}}
		stage('Build'){
		  steps {
			sh '/home/chetan/Documents/DevOps_Tool/apache-maven-3.9.2-bin/apache-maven-3.9.2/bin/mvn install'
			}}
		stage('Deployment'){
		  steps {
			sh 'cp target/Apple.war /home/chetan/Documents/DevOps_Tool/apache-tomcat-9.0.75/webapps'
			}
}}}
