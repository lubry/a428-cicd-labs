    pipeline {
        agent {
            docker {
                image 'node:lts-bullseye-slim'
                args '-p 3000:3000'
            }
        }
        stages {
            stage('Build') {
                steps {
                    sh 'npm install'
                }
            }
            stage('Test') { 
                steps {
                    sh './jenkins/scripts/test.sh' 
                }
            }
            stage('Deploy') { 
    	        steps {
                sh './jenkins/scripts/deliver.sh'
		}
		steps {
                echo "Wait a minutes"
                sleep(time: 6, unit: "SECONDS")
            }
	   stage('End') {
		steps {
		sh './jenkins/scripts/kill.sh' 
                } 
            }
        }
    }
}
