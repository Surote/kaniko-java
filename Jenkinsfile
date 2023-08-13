pipeline {
  agent {
      kubernetes{
          label 'test'
      }
  }
  stages {
    stage('Build-Jar-file') {
      steps {
        container('maven') {
          sh 'mvn package'
        }
      }
    }
    stage('Build-Docker-Image') {
      steps {
        container('kaniko') {
          sh '''/kaniko/executor --context `pwd` --destination surote/kaniko-hello:2.0'''
        }
      }
    }
  }
}

