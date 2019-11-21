pipeline {
  agent any
  stages {
      when {
          changeset 'images/*'
          beforeAgent true
            stage('build') {
                steps {
                sh 'ls'
            }
      }
    }
  }
}
