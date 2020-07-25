pipeline {
  agent any
  stages {
    stage('Lint HTML') {
      steps {
        sh 'tidy -q -e *.html'
      }
    }

    stage('Upload to AWS') {
      steps {
        withAWS(credentials: 'aws-static') {
          retry(count: 2) {
            s3Upload(bucket: 'mohamed-project3', includePathPattern: '*.html')
          }

        }

      }
    }
  }
}
