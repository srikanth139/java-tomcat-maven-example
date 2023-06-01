pipeline {
	agent any
	stages {		
		
		stage ("CI Project"){
			steps {
				bat 'mvn clean install'
			}
			post {
			success {
			echo "Now Archiving ----"
			archiveArtifacts artifacts : '**/*.war'
				}
			}
		}
		stage ("Dev CD Pipeline"){
			steps{
			build job : 'Dev-CD-Pipeline'
			}
		}
	}
}
