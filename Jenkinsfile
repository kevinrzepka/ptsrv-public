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
               }
            }
        }
       stage('Build') {
           steps {
               script {
                   def runId = env.BUILD_CHECK_ID
                   startCheckRun(this, runId)
                   echo "pseudo build"
                   passCheckRun(this, runId)
               }
           }
       }
        stage('Test') {
           steps {
               script {
                   def runId = env.TEST_CHECK_ID
                   startCheckRun(this, runId)
                   echo "pseudo build"
                   failtCheckRun(this, runId)
               }
           }
       }
    }
}
