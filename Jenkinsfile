pipeline {
    agent any
    
	tools {
        maven 'maven-3.9.11'
    }
    
    stages {
        stage('Build') {
            steps {
                echo 'Building the application...'
                
                script {
                    withCredentials([string(credentialsId: 'mulesoft-key', variable: 'MULESOFT_KEY')]) {
		                sh '''
		                mvn -o clean package \
		                  -Denv=local \
		                  -Dmulesoft.key=${MULESOFT_KEY} \
		                  -DskipTests
		                '''
                    }
                }
            }
        }

        stage("test") {
            steps {
                echo 'Testing the application...'
                
                script {
                    withCredentials([string(credentialsId: 'mulesoft-key', variable: 'MULESOFT_KEY')]) {
		                sh '''
		                mvn -o  clean test \
		                  -Denv=local \
		                  -Dmulesoft.key=${MULESOFT_KEY}
		                '''
                    }
                }
            }
            post {
                always {
                    publishHTML([
                        reportDir: 'target/site/munit/coverage',
                        reportFiles: 'summary.html',
                        reportName: 'MUnit-Coverage-Report',
                        keepAll: true,
                        alwaysLinkToLastBuild: true,
                        allowMissing: false
                    ])
                }
            }
        }

        stage("deploy") {
            steps {
                echo 'deploying the application... To noone'
            }
        }
    }
}
