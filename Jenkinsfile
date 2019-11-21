pipeline {
  agent any
  stages {
      stage('build') {
        /*when{
            changeset 'images/*'
        }
       */
        steps {


            //cfiles=`git show --pretty="" --name-only`
            def gitCommit = sh(returnStdout: true, script: 'git show --pretty="" --name-only').trim()
        }
      }
    }
  }

