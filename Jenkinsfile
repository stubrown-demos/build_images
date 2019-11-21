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
                currentBuild.rawBuild.getChangeSets().each { cs ->
                    cs.getItems().each { item ->
                        item.getAffectedFiles().each { f ->
                            println f
                        }
                    }
                }

            }
        }
      }
    }
  }

