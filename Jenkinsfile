pipeline{
    agent any
    stages{
        stage('download'){
            steps{
              checkout([$class: 'GitSCM', branches: [[name: '*/feat01']], extensions: [], userRemoteConfigs: [[credentialsId: '8494ffb9-293a-40d2-a488-a123e8807c37', url: 'https://github.com/venkateswarareddypondugula9/mavenrepo.git']]])
            }
        }
        stage('build'){
            steps{
             sh 'mvn package'   
            }
        }
        stage('sonar'){
            steps{
               withSonarQubeEnv('sonarqube') {
                   sh 'mvn sonar:sonar'
                }
            }
        }
        
    }
}    
