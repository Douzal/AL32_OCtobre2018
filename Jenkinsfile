pipeline {
  agent any
  stages {
    stage('Receuperation des sources GIT') {
      steps {
        git(url: 'https://github.com/Douzal/AL32_OCtobre2018.git', branch: 'master', credentialsId: 'loginGithub')
      }
    }
  }
}