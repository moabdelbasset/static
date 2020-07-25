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

    stage('Validate deployment') {
      steps {
        sh '''
                    response=$(curl -s -o /dev/null -w "%{http_code}
" http://mohamed-project3.s3-website.us-east-2.amazonaws.com/)
                    if [ "$response" != "200" ]
                    then
                        exit 1
                    fi
                '''
      }
    }

  }
}
