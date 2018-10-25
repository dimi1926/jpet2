pipeline {
  agent any
  stages {
    stage('git') {
      steps {
        git(credentialsId: '454448ca7fd1f14b10916e0a6dee10bc010cee58', branch: 'master', url: 'https://github.com/dimi1926/jpet2.git')
      }
    }
    stage('') {
      steps {
        powershell 'runmaven.bat'
      }
    }
  }
}