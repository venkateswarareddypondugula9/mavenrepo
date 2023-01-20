node('slave') {
    stage('download') {
      git branch: 'feat01', changelog: false, credentialsId: 'be276873-5523-450e-994d-6e7573f41ac6', poll: false, url: 'https://github.com/venkateswarareddypondugula9/mavenrepo.git'
}
    stage('build') {
      sh 'mvn package'
}
    stage('permission') {
      input 'approve/deny'
}
    stage('deploy') {
      sh 'scp /root/workspace/sample/target/studentapp-2.1.1-FEAT01-SNAPSHOT.war root@65.0.74.90:/var/lib/tomcat/webapps'
}   
    stage('sonar'){
        withSonarQubeEnv('sonarqube') {
            sh 'mvn sonar:sonar'
        }
}
    stage('Email') {
        emailext body: 'test build', subject: 'Test build', to: 'pondugulabhargavi145@gmail.com'
    }
}
