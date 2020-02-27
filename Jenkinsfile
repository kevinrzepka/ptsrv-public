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
                    env.BUILD_CHECK_ID = createCheckRun(this, 'build')
                    env.TEST_CHECK_ID = createCheckRun(this, 'test')
                    updateCheckRun(this, runId, 'success')
               }
            }
        }
       stage('Build') {
           steps {
               script {
                   passCheckRun(this, "${env.BUILD_CHECK_ID}")
               }
           }
       }
        stage('Test') {
           steps {
               script {
                   failCheckRun(this, "${env.TEST_CHECK_ID}")
               }
           }
       }
    }
}
