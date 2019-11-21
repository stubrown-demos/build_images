pipeline {
  agent any
  stages {
      stage('build') {
        /*when{
            changeset 'images/*'
        }
       */
        steps {

            script {
                //cfiles=`git show --pretty="" --name-only`
                environment {
                    COMMIT_FILES = sh(script: 'pwd', , returnStdout: true).trim()

                }
                echo "${COMMIT_FILES}"
            }
        }
      }
    }
  }

