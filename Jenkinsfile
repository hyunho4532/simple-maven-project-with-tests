node('master') {
  checkout scm

  stage('Build') {
	  withMaven(globalMavenSettingsConfig: '', jdk: '', maven: 'M3', mavenSettingsConfig: '', traceability: true) {
      if (isUnix()) {
        sh 'mvn -Dmaven.test.failure.ignore clean package'
      } else {
        bat 'mvn -Dmaven.test.failure.ignore clean package'
      }
	  }
  }
  
  stage('Results') {
    junit '**/target/surefire-reports/TEST-*.xml'
    archive 'target/*.jar'
  }
}
