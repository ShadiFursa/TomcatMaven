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

	}
}

