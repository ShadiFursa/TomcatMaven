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
				deploy adapters: [tomcat9(credentialsId: '2875d8aa-3ec6-4e8c-adce-a41f02384e4b', path: '', url: 'https://34.254.159.229:8888/')], contextPath: null, war: '**/*.war'
			}

		}

	}
}

