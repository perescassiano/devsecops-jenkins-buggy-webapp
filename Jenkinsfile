pipeline {
  agent any
  tools { 
        maven 'Maven_3_5_2'  
    }
   stages{
    stage('CompileandRunSonarAnalysis') {
            steps {	
		sh 'mvn clean verify sonar:sonar -Dsonar.projectKey=awsjenkinsbuggywebapp -Dsonar.organization=awsjenkinsbuggywebapp -Dsonar.host.url=https://sonarcloud.io -Dsonar.login=14daa0420929a86483320a61281aea0297438219'
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
