pipeline {
	agent any
	
	stages{
		stage('Checkout Code'){
			steps{
				checkout scm
				}
			}
	
	stage('Build'){
		steps{
			bat "mvn clean install -Dmaven.test.skip=true"
		}
	}
	
	stage('Archive Artifact'){
		steps{
		archiveArtifacts artifacts:'target/*.war'
		}
	}
	
	// stage('deployment'){
	// 	steps{
	// 	//deploy adapters: [tomcat9(credentialsId: 'TomcatCreds' path: '', url: 'http://52.90.187.236:8080/')], contextPath: 'counterwebapp', war: 'target/*.war'
	// 	deploy adapters: [tomcat9(url: 'http://3.92.185.199:8080/', 
 //                              credentialsId: 'TomcatCreds')], 
 //                     war: 'target/*.war',
 //                     contextPath: 'app'
	// 	}
		
	// }
	
	stage('Notification'){
		steps{
		emailext(
			subject: "Job Completed",
			body: "Jenkins pipeline job for maven build job completed",
			to: "ajaynano.ajay7@gmail.com"
		)
		}
	}
	}
}
