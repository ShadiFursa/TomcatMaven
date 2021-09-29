pipeline{
	agent any;
	stages{
		stage('Clone the repo'){
			steps{
				git 'https://github.com/jleetutorial/maven-project.git'

			}
		}
		stage('Build Project'){
			steps{
				sh 'mvn clean install'
			}
		}
		stage('Add war to archive'){
			steps{
				archiveArtifacts artifacts: '**/*.war', followSymlinks: false


			}
		}
		stage('Copy artifact from archives'){
			steps{
				copyArtifacts filter: '**/*.war', fingerprintArtifacts: true, projectName: 'MavenBD', selector: lastSuccessful()
			}
		}
		stage('Deploy to tomcat containter'){
			steps{
				deploy adapters: [tomcat9(credentialsId: '2875d8aa-3ec6-4e8c-adce-a41f02384e4b', path: '', url: 'http://172.31.5.224:8888/')], contextPath: null, war: '**/*.war'
			}

		}

	}
}

