pipeline {
  agent {
    node {
      label 'any'
    }

  }
  stages {
    stage('Init gopath') {
      steps {
        sh 'sh \'mkdir -p $GOPATH/{bin,pkg,src}\''
      }
    }
    stage('Build go proejct') {
      steps {
        sh 'sh \'cd ${PROJ_DIR}/daemon/example; go test && go build && go install\''
      }
    }
    stage('Deploy to test') {
      steps {
        input(message: 'deploy to test ?', ok: 'De', id: '1')
      }
    }
  }
  environment {
    PROJ_DIR = 'src/learningGo'
  }
}