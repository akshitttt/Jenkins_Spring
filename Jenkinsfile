pipeline{
    agent any
    tools{
        maven 'maven'
    }
    stages{
        stage('Checkout SCM'){
            steps{
                git url: 'https://github.com/akshitttt/Jenkins_Spring.git'
            }
        }
        stage('Build'){
            steps{
                echo "Running Job: ${env.JOB_NAME}\n build: ${env.BUILD_ID}"
                sh 'mvn -f ./pom1.xml clean install package'
            }
            post{
                success{
                    archiveArtifacts(artifacts: 'target/*.war', allowEmptyArchive: true)
                }
            }
		}
	}
	post{
		failure{
                mail to: 'akshit075@gmail.com',
                from: 'akshit075@gmail.com',
                subject: "Project Build: ${env.JOB_NAME} - Failed",
                body: "Job Failed -  \"${env.JOB_NAME} \" build: ${env.BUILD_NUMBER}"
            }
		success{
                    emailext attachmentsPattern: "*target/*.war",
                    body: '''${SCRIPT, template="groovy-template"}''',
                    subject: "Project Build: ${env.JOB_NAME} - SUCCESS",
                    mimeType: 'text/html',
                    to: 'akshit075@gmail.com'
            }
	}
}