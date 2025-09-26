pipeline {
    agent any
    
	tools {
        maven 'maven-3.9.11'
    }
    
    stages {
        stage('Build') {
            steps {
                echo 'Building the application...'
                
                sh '''
                mvn -o clean package \
                  -Denv=local \
                  -Dmulesoft.key=MyMockMulesofKey \
                  -DskipTests
                '''
            }
        }

        stage("test") {
            steps {
            
                echo 'Testing the application...'
            
                sh '''
                mvn -o  clean test \
                  -Denv=local \
                  -Dmulesoft.key=MyMockMulesofKey
                '''
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
