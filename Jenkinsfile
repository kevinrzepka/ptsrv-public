pipeline {
    
    environment {
        GITHUB_APP_ID = '54577'
        GITHUB_REPO_OWNER = 'kevinrzepka'
        GITHUB_REPO_NAME = 'ptsrv-public'
    }
    
   agent any

   stages {
      stage('Setup') {
          steps {
               script {
                    sh 'env | sort'
                    def runId = createCheckRun(this, 'test')
                    updateCheckRun(this, runId, 'success')
               }
            }
        }
    }
}
