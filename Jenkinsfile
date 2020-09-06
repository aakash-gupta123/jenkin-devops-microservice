pipeline {
	//agent any
	agent { 
		docker { 
			//image 'maven:3.6.3'
			image 'node:14.9'
		} 
	}
	agent { 
		docker { 
			image 'maven:3.6.3'
		} 
	}
	stages {
		stage('Build'){
			steps{
				//echo "build"
				sh 'mvn --version'
				sh 'node --version'
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
