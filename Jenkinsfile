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
				script{
					"./mvnw package"
				}

			}
		}
		stage('Add to archive'){
			archiveArtifacts artifacts: 'build/libs/**/*.war', followSymlinks: false
		}
	}
}

