pipeline{
agent any
stages{
	stage('GetCode'){
		steps{
			git 'https://github.com/com-satya/sonarqube_testing.git'
		}
	}
	stage('Build'){
		steps{
			sh 'mvn clean pacakage'
		}
	}
	stage('SonarQube analysis'){
		steps{
		withSonarQubeEnv('sonarqube-server'){
			sh 'mvn sonar:sonar'
			}
		}
	}
}
}
