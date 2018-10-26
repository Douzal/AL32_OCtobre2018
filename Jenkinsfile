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
    
    //rajout qualimetrie
    stage('qualimetrie') {
      steps {
        bat(script: 'mvnrun.bat', encoding: 'utf-8')
      }
    }

// Rajout dans le Jenkinsfile
    stage('Publication') {
        steps {
          nexusArtifactUploader artifacts: [
            [artifactId: 'jpetstore', classifier: 'debug', file: 'target/jpetstore.war', type: 'war']
          ],
            credentialsId: 'idNexus',
            groupId: 'jpetstore',
            nexusUrl: 'localhost:8081/',
            nexusVersion:     'nexus3',
            protocol: 'http',
            repository: 'maven-snapshots',
            version: '1.0-SNAPSHOT'
            }
        }
    }
  }