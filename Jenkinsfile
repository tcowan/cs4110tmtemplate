// Jenkinsfile for Turing Machine in CS 4110
pipeline {
	agent {
        node { label 'master' }
	}

	stages {
		stage('Build') {
			steps {
				echo 'Building..'
				//##############################################################
				// Uncomment exactly one of the "sh" lines below and change 
				//   PATHTOSOURCE to the relative path to your source file.
				// 

				//sh 'cs4110turingmachinebuild script "./PATHTOSOURCE"'
				//sh 'cs4110turingmachinebuild swift "./PATHTOSOURCE"'
				//sh 'cs4110turingmachinebuild java "./PATHTOSOURCE"'
				//sh 'cs4110turingmachinebuild c# "./PATHTOSOURCE"'

				// Touch nothing else in this file or receive a failing grade.
				//##############################################################
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
