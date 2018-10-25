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
        bat(script: 'mvnrun.md', encoding: 'utf-8')
      }
    }
  }
}