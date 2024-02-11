pipeline {
    agent { label 'Jenkins-Agent' }
    tools {
        jdk 'java21'
        maven 'maven3'
    }

stages{
        stage("Cleanup Workspace"){
                steps {
                cleanWs()
                }
        }

stage("Checkout from SCM"){
                steps {
                    git branch: 'main', credentialsId: 'github', url: 'https://github.com/emailtokunaljha/jenkins-clone-1'
                }
}
 stage("Build Application"){
         steps {
             sh "mvn clean package"
         }
}

     stage("Test Application"){
           steps {
                 sh "mvn test"
           }
       }

         stage("SonarQube Analysis"){
           steps {
	           script {
		        withSonarQubeEnv(credentialsId: 'jenkins-sonarcube-token') { 
                        sh "mvn sonar:sonar"
		        }
	           }	
           }
       }
    
}
}
