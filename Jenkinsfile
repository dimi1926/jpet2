pipeline {
  agent any
  stages {
    stage('Recuperation') {
      steps {
       git( url: 'https://github.com/dimi1926/jpet2.git',  branch: 'master', credentialsId: 'loginGithub')

      }
    }
    stage('Maven install') {
      steps {
        bat(encoding: 'utf-8', script: 'runmaven.bat')
      }
    }
    stage('Qualimetrie') {
      steps {
        withSonarQubeEnv('SonarQubeEnv'){
          bat(encoding: 'utf-8', script: 'runsonar.bat')
        }
        
      }
    }
    stage('Quality Gate') {
      steps {
        sleep 10
          timeout(time: 4, unit: 'MINUTES') {
                    waitForQualityGate abortPipeline: true
                }
          }
    }
    stage('Publication') {
      steps {
        nexusArtifactUploader(artifacts: [
                         [ artifactId:'jpetstore', type:'war', classifier:'debug', file:'target/jpetstore.war']
                    ], credentialsId: 'AdminNexus', groupId: 'jpetstore', nexusUrl: 'localhost:8081/', nexusVersion: 'nexus3', protocol: 'http', repository: 'maven-snapshots', version: '1.0-SNAPSHOT')
        }
      }
    }
  }



