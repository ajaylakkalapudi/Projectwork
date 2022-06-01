pipeline{
	    agent any
	    tools{
	        maven 'maven'
	    }
	    stages{
	        stage("checkout the code from github"){
	            steps{
	               git branch: 'main', credentialsId: 'jenkins', url: 'https://github.com/Srilekha845/finalproject.git'
	            }
	        }
	        stage("build the code by using maven"){
	            steps{
	                sh 'mvn clean package'
	            }
	        }
	     
	    }
	}


