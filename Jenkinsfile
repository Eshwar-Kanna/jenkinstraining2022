pipeline {

	agent { label "linuxbuildnode" }
		stages {
			stage("SCM"){

				steps { 
					echo "pulling the code from github " 
					git "https://github.com/Eshwar-Kanna/simple-java-maven-jenkins2022.git "
					}
				}
			stage("build"){
				steps{ 
					echo "build code"
		
					}
				}
			stage("test"){
				steps{
					echo "code tested and approved"
					}
				}
			
			stage("deploy") {
				steps{
					echo "code is depolying in the production"
				
					}
				}
			}

	}
