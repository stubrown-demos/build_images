pipeline {
  agent any
  stages {
    stage('Process Image') {
      /*when{
        changeset 'images/*'
      }
      */
       environment {
           COMMIT_FILES = sh(script: 'git show --pretty="" --name-only', , returnStdout: true).trim()
       }
          steps {
                sh 'echo found "[${COMMIT_FILES}"]'
            }
      }
  }
}


