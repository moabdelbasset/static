pipeline {
  agent any
  stages {
    stage('Upload to AWS ') {
      steps {
        withAWS(credentials: 'Moh123@@@') {
          retry(count: 2) {
            s3Upload(bucket: 'mohamed-project3', includePathPattern: '*.html')
          }

        }

      }
    }

  }
}
