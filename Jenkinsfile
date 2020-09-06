pipeline {
	agent any
	environment {
		dockerHome = tool 'my-docker'
		mavenHome = tool 'maven-3.6.3'
		PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
	}
	stages{
		stage('Checkout'){
			steps{
				sh 'mvn --version'
				sh 'docker --version'
				echo "Build"
				echo "PATH - $PATH"
				echo "BUILD_NUMBER - $env.BUILD_NUMBER"
				echo "BUILD_DIR - $env.BUILD_DIR"
				echo "BUILD_TAG - $env.BUILD_TAG"
				echo "BUILD_URL - $env.BUILD_URL"
			}
		}
		stage('Compile'){
			steps{
				sh 'mvn clean compile'
			}
		}
		stage('Test'){
			steps{
				sh 'mvn test'
			}
		}
		stage('Integration Test'){
			steps{
				sh 'mvn failsafe:integration-test failsafe:verify'
			}
		}
		stage('Package'){
			steps{
				sh 'mvn package -DskipTests'
			}
		}
		stage('Build Docker Image'){
			steps{
				script{
					dockerImage = docker.build("aakashgupta/currency-exchange-devops:${env.BUILD_TAG}")
				}
			}
		}
		stage('Push Docker Image'){
			steps{
				script{
					docker.withRegistry('', 'dockerhub'){
						dockerImage.push();
						dockerImage.push('latest');
					}
				}
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
