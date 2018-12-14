pipeline {
  agent any
  stages {
    stage('open project') {
      agent any
      steps {
        sh '''#! /bin/bash








git clone https://github.com/AnnaGats/Test-project.git








cd Test-project




cd test




export PATH="/usr/local/bin:/usr/local/sbin:~/bin:$PATH"




gradle build
gradle build -x test








cd build
cd libs
mv test-1.0-SNAPSHOT.war /Library/Tomcat/webapps/




cd ~anna
cd Desktop
cd Test-project
cd test




export PATH="/usr/local/bin:/usr/local/sbin:~/bin:$PATH"












cd /Library/Tomcat/webapps








mv test-1.0-SNAPSHOT.war ROOT.war




cd /Library/Tomcat/bin
./startup.sh




open http://localhost:8080
'''
      }
    }
  }
}