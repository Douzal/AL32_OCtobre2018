pipeline {
  agent any
  stages {
    stage('Receuperation des sources GIT') {
      steps {
        git(url: 'https://github.com/Douzal/AL32_OCtobre2018.git', branch: 'master', credentialsId: 'loginGithub')
      }
    }
    stage('Build MAVEN / Windows Batch Script') {
      steps {
        bat(script: 'runmaven.bat', encoding: 'utf-8')
      }
    }
  }
}