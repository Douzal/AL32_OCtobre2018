pipeline {
  agent any
  stages {
    stage('Receuperation des sources GIT') {
      steps {
        git(url: 'https://github.com/Douzal/JpetStore.git', branch: 'master', credentialsId: 'loginGithub')
      }
    }
    stage('Build MAVEN / Windows Batch Script') {
      steps {
        bat(script: 'mvnrun.bat', encoding: 'utf-8')
      }
    }

// Rajout dans le Jenkinsfile
    stage('Publication') {
        steps {
          nexusArtifactUploader {
            nexusVersion('nexus3')
            protocol('http')
            nexusUrl('localhost:8081/')
            groupId('jpetstore')
            version('1.0')
            repository('maven-snapshots')
            credentialsId('idNexus')
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