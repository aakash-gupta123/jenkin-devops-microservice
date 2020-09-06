pipeline {
	agent any
	stages {
		stage('Build'){
			steps{
				echo "build"
			}
		}
		stage('test'){
			steps{
				echo "test"
			}
		}
		stage('integration test'){
			steps{
				echo "integration test"
			}
		}		
	}

	post {
		always{
			echo "always executed!"
		}
		success{
			echo "Only when I am successful"
		}
		failure{
			echo "Only when I am failure"
		}
	}
}
