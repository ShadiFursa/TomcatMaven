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

	}
}

