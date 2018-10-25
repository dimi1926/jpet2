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
    stage('Publication') {
      steps {
        nexusArtifactUploader {
          nexusVersion('nexus3')
          protocol('http')
          nexusUrl('localhost:8081/')
          groupId('jpetstore')
          version('1.0')
          repository('maven-snapshots')
          credentialsId('loginNexus')
          artifact {
              artifactId('jpetstore')
              type('war')
              classifier('debug')
              file('target/jpetstore.war')
          }
        }
      }
    }
  }
}
