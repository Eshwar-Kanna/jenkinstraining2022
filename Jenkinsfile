pipeline {

	agent any 
		stages {
			stage("SCM"){

				steps { echo "git pull my code " }
				}
			stage("build"){
				steps{ echo "git build code"}
				}
			stage("test"){
				steps{echo " git test my code"}
				}
			stage("deploy") {
				steps{echo "git depoly my code"}
				}
			}

	}
