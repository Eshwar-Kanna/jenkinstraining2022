pipeline {

	agent any 
		stages {
			stage("SCM"){

				steps { 
					echo "pulling the code from github " 
					git "https://github.com/vimallinuxworld13/simple-java-maven-app.git"
					}
				}
			stage("build"){
				steps{ 
					echo " build code"
					sh ' mvn clean package '
					}
				}
			stage("test"){
				steps{echo " code tested and approved"}
				}
			
			stage("deploy") {
				steps{
					echo "code is depolying in the production"
					sh "java - jar target/*.jar"
				
					}
				}
			}

	}
