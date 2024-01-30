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
                    git branch: 'main', credentialsId: 'github', url: 'https://github.com/emailtokunaljha/jenkins'
                }
}
 stage("Build Application"){
         steps {
             sh "mvn clean package"
         }
}
}
}
