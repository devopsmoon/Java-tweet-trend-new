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
    }
}