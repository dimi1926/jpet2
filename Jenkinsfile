pipeline {
  agent any
  stages {
    stage('git') {
      steps {
        git(credentialsId: 'a87a4bc79b31fab025a25c179d3a7e1700aaf4f8', branch: 'master', url: 'https://github.com/dimi1926/jpet2.git')
      }
    }
    stage('error') {
      steps {
        powershell 'runmaven.bat'
      }
    }
  }
}