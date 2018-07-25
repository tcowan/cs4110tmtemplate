// Jenkinsfile for Turing Machine in CS 4110
pipeline {
	agent any

	stages {
		stage('Build') {
			steps {
				echo 'Building..'
				sh 'javac TuringMachine.java'
			}
			post {
				failure {
					echo 'Sending console log to submitter'
					sh 'cs4110sendlog "Turing Machine Build failed"'
				}
			}
		}
		stage('Test') {
			steps {
				echo 'Testing..'
				sh 'cs4110cucumber'
			}
			post {
				always {
					echo 'Reporting to the student....'
					sh "cs4110report"
					echo 'Grading the assignment....'
					sh "cs4110grade"
				}
			}
		}
	}
}
