pipeline {
  agent any
  stages {
      stage('build') {
        /*when{
            changeset 'images/*'
        }
       */
          environment {
              COMMIT_FILES = sh(script: 'git show --pretty="" --name-only', , returnStdout: true).trim()

          }
        steps {


                //cfiles=`git show --pretty="" --name-only`

                sh 'echo "${COMMIT_FILES}"'
            }
      }
  }
}


