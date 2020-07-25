pipeline {
    agent any
    stages {
        stage('Upload to AWS ') {
            steps {
                withAWS(credentials:'M0h123aym') {
                    retry(2) {
                        s3Upload(bucket:"mohamed-project3", path:'', includePathPattern:'*.html')
                    }
                }
            }    
        }    
    }
}    
