stages{
	stage('GetCode'){
		steps{
			git 'https://github.com/com-satya/sonarqube_testing.git'
		}
	}
	stage('Build maven'){
            steps{
                script{
                    withMaven(maven: 'Maven3') {
                     sh 'java --version'        
                     sh 'mvn --version'
                     sh 'mvn clean package'
                }
                    
                }
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
