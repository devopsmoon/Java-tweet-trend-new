pipeline{
    agent any

    tools{
        maven 'maven'
    }
    stages{
        stage('Checkout'){
            steps{
                git branch: 'main', credentialsId: 'Jenkins-user', url: 'git@github.com:devopsmoon/Java-tweet-trend-new.git'
            }
        }
        stage('Build'){
            steps{
                sh "mvn install"
            }
        }
        stage('Sonar Analysis'){
            steps{
                withSonarQubeEnv(installationName: 'sonar',credentialsId: 'sonar'){
                    sh "mvn sonar:sonar"

                }
            }
        }
        stage('Nexus pull'){
            steps{
                nexusArtifactUploader artifacts: [
[
artifactId: 'spring-boot-starter-parent', 
classifier: '', 
file: '/var/lib/jenkins/.m2/repository/com/valaxy/demo-workshop/2.1.2/demo-workshop-2.1.2.jar', 
type: 'jar'
]
], 
credentialsId: 'admin', 
groupId: 'com.valaxy', 
nexusUrl: '54.144.157.174:8081', 
nexusVersion: 'nexus3', 
protocol: 'http', 
repository: 'Java-App-Repo/', 
version: '2.2.0.RELEASE'
            }
        }
    }
}