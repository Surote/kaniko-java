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
        timeout(time: 15, unit: "MINUTES") {
	        input message: 'Do you want to approve the build?', ok: 'Yes'
	}
        container('kaniko') {
          sh '''/kaniko/executor --context `pwd` --destination surote/kaniko-hello:2.0'''
        }
      }
    }
  }
}

