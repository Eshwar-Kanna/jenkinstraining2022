pipeline {
    
    		agent {
        			label "linuxbuildnode"
    			}
    
    
    		stages {
       			stage('SCM') {
            				steps {
                			git 'https://github.com/Eshwar-Kanna/jenkins-docker-java-maven.git '
                
           					 }
            
       				 }
        
        			stage('Build by Maven Package') {
            				steps {
                					sh 'mvn clean package'
            					}
            
       				 }
        
        
       			 stage('Build Docker OWN image') {
            				steps {
               			 sh "sudo docker build -t  eshwar29/javaweb:${BUILD_TAG}  ."
                			//sh 'whoami'
           					 }
            
       				 }
        
        
        			stage('Push Image to Docker HUB') {
            				steps {
                
                			withCredentials([string(credentialsId: 'DOCKER_PAASWD', variable: 'DOCKER_HUB_PASSWORD')]) {
                 			sh "sudo docker login -u eshwar29 -p $DOCKER_HUB_PASSWORD"
			}
               
               			sh "sudo docker push eshwar29/javaweb:${BUILD_TAG}"
           				 	}
            
        				}
        
        
       			 stage('Deploy webAPP in DEV Env') {
            				steps {
                			sh 'sudo docker rm -f myjavaapp'
                			sh "sudo docker run  -d  -p  8080:8080 --name myjavaapp   eshwar29/javaweb:${BUILD_TAG}"
                			//sh 'whoami'
            					}
            
        				}
        
        
        			stage('Deploy webAPP in QA/Test Env') {
            				steps {
               
               				sshagent(['QA_ENV_SSH_CRED']) {
    
                    				sh "ssh  -o  StrictHostKeyChecking=no ec2-user@13.233.100.238 sudo docker rm -f myjavaapp"
                    				sh "ssh ec2-user@13.233.100.238 sudo docker run  -d  -p  8080:8080 --name myjavaapp   eshwar29/javaweb:${BUILD_TAG}"
                						}
