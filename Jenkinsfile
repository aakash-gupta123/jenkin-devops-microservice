pipeline {
	/*
	//agent any
	agent { 
		docker { 
			//image 'maven:3.6.3'
			image 'node:14.9'
		} 
	}
	stages {
		stage('Build'){
			steps{
				//echo "build"
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
*/
 agent none
    stages {
        stage('Back-end') {
            agent {
                docker { image 'maven:3.6.3' }
            }
            steps {
                sh 'mvn --version'
            }
        }
        stage('Front-end') {
            agent {
                docker { image 'node:14.9' }
            }
            steps {
                sh 'node --version'
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
