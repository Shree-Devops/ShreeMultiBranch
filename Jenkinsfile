pipeline{
agent any
environment{
	ART_URL=''
}
options {
	disableConcurrentBuilds(); //disable parallel builds
	retry(1)
}
	stages{
		stage('checkout'){
			steps{
				echo 'checking out!!'
				git 'https://github.com/Shree-Devops/JenkinsPractice.git'
			}
		}
		stage('build'){
			steps{
				echo 'Building!!'
				script{
					env.PATH = "C:/Users/ShreeMohini_Baghel/apache-maven-3.9.4/bin;c:\\Windows\\System32"
				}
        		bat label: '', script: 'mvn package'
			}
		}
		stage('archive'){
			steps{
				echo 'Archiving!!'
				archiveArtifacts 'target/*.jar'
			}
		}
	}
	post{
		always{
			echo 'Pipeline finished'
			step([$class: 'JUnitResultArchiver', testResults: '**/target/surefire-reports/*.xml'])
		}
	}
}
