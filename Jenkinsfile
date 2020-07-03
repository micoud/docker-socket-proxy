pipeline {
  agent any

  environment {
    REGISTRY="registry.cta-test.zeuthen.desy.de"
  }

  stages {
    stage('Build container') {
      steps {
        sh '''docker build \
          --build-arg VCS_REF="$GIT_SHA1" \
          --build-arg BUILD_DATE="$(date --rfc-3339 ns)" \
          -t ${REGISTRY}/docker-socket-proxy:latest .'''
      }
    }

    stage('Push container to registry') {
      steps {
        sh "docker push ${REGISTRY}/docker-socket-proxy:latest"
      }
    }
  }
}
