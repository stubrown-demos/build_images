pipeline {
  agent any
  stages {
      stage('build') {
        when{
            changeset 'images/*'
        }
        steps {

            sh 'ls'
            println(currentBuild.changeSets)
            script {
                def changeSet = build.getChangeSet();

                changeSet.getItems();

            }
        }
      }
    }
  }

