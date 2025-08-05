pipeline {
  agent any
  tools { 
        maven 'Maven_3_8_9'  
    }
   stages{
    stage('CompileandRunSonarAnalysis') {
            steps {	
		sh 'mvn clean verify sonar:sonar -Dsonar.projectKey=sexysalim -Dsonar.organization=sexysalim -Dsonar.host.url=https://sonarcloud.io -Dsonar.token=603f73f0ac5050f4aa876dcb66533fa2e026de9b'
			}
    }

	stage('RunSCAAnalysisUsingSnyk') {
            steps {		
				withCredentials([string(credentialsId: 'SNYK_TOKEN', variable: 'SNYK_TOKEN')]) {
					sh 'mvn snyk:test -fn'
				}
			}
    }		
  }
}
