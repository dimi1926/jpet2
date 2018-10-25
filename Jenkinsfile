pipeline {
  agent any
  stages {
    stage('git') {
      steps {
        git(credentialsId: 'loginGithub', branch: 'master', url: 'https://github.com/dimi1926/jpet2.git')
      }
    }
    stage('run') {
      steps {
        powershell(script: 'runmaven.bat', encoding: 'utf-8')
      }
    }
  }
}