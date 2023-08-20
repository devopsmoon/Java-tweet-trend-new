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
    }
}