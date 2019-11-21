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
                def gitCommit = sh(returnStdout: true, script: 'git show --pretty="" --name-only').trim()
                echo '${gitCommit}'
            }
        }
      }
    }
  }

