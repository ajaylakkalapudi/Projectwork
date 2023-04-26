
pipeline{
	    agent any
	    tools{
	        maven 'maven'
	    }
	    stages{
	        stage("checkout the code from github"){
	            steps{
	              git branch: 'main', credentialsId: 'jenkins', url: 'https://github.com/ajaylakkalapudi/Projectwork.git'
	            }
	        }
		
	        stage("build the code by using maven"){
	            steps{
	                sh 'mvn clean package'
	            }
	        }
	        stage("deploy the code to tomcat8"){
	            steps{
	                sshagent(['tomcat']){
	                    //rename the war file
	                    sh "mv target/*.war target/myweb.war"
	                    //copy war file into tomcat server
	                    sh "scp -o StrictHostKeyChecking=no target/myweb.war ec2-user@172.31.41.8:/opt/tomcat9/webapps"
	                    //start and stop the tomcat8
	                    sh "ssh ec2-user@172.31.41.8 /opt/tomcat9/bin/shutdown.sh"
	                    sh "ssh ec2-user@172.31.41.8 /opt/tomcat9/bin/startup.sh"
	                }
	            }
	        }
		
	    }
	}
