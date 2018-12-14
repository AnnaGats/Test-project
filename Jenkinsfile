pipeline {
  agent any
  stages {
    stage('setting path for homebrew') {
      agent any
      steps {
        sh '''export PATH="/usr/local/bin:/usr/local/sbin:~/bin:$PATH"
'''
      }
    }
    stage('copy project from github') {
      steps {
        sh '''git clone https://github.com/AnnaGats/Test-project.git

cd Test-project

cd test'''
      }
    }
    stage('gradle build') {
      steps {
        sh 'gradle build -x test'
      }
    }
    stage('moving war file to Tomcat folder') {
      steps {
        sh '''cd build
cd libs
mv test-1.0-SNAPSHOT.war /Library/Tomcat/webapps/
'''
      }
    }
    stage('db backup') {
      steps {
        sh '''cd ~ anna
cd Desktop
cd Test-project
cd test
psql -U postgres -d easypay_db < 2.sql'''
      }
    }
    stage('rename war file') {
      steps {
        sh '''cd /Library/Tomcat/webapps
mv ROOT.war new.war
mv test-1.0-SNAPSHOT.war ROOT.war'''
      }
    }
    stage('deploy project') {
      steps {
        sh '''d /Library/Tomcat/bin
./startup.sh'''
      }
    }
    stage('open browser') {
      steps {
        sh 'open http://localhost:8080'
      }
    }
  }
}