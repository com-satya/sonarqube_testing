pipeline{
agent any
stages{
	stage('GetCode'){
		steps{
			 checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/com-satya/sonarqube_testing.git']]])
            }
			
		}
	
	stage('Build maven'){
            steps{
                script{
                    withMaven(maven: 'Maven3') {
                     sh 'java --version'        
                     sh 'mvn --version'
                     sh 'mvn clean compile install'
                }
                    
                }
            }
        }
	stage('SonarQube analysis'){
		steps{
		
		
		withMaven(maven: 'Maven3'){
    withSonarQubeEnv('sonarqube-server') {
        sh '''mvn sonar:sonar  \
  -Dsonar.projectKey=sonarqube \
  -Dsonar.projectName=sonarqube \
  -Dsonar.host.url=http://ec2-3-72-243-136.eu-central-1.compute.amazonaws.com:9000 \
  -Dsonar.sourceEncoding=UTF-8 \
  -Dsonar.language=java \
  -Dsonar.sources=/var/jenkins_home/workspace/sonarqube_test/ \
  -Dsonar.java.binaries=/opt/sonarqube/web/WEB-INF/classes'''

    }
      }
		
			}
		}
	
}
}
