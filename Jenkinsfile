pipeline {
    agent {
        kubernetes {
            label 'kaniko'
            defaultContainer 'jnlp'
            yaml """
apiVersion: v1
kind: Pod
metadata:
  labels:
    some-label: some-label-value
spec:
  containers:
  - name: kaniko
    image: gcr.io/kaniko-project/executor:debug
    command:
    - /busybox/cat
    tty: true
    volumeMounts:
      - name: jenkins-docker-cfg
        mountPath: /kaniko/.docker
  volumes:
  - name: jenkins-docker-cfg
    projected:
      sources:
      - secret:
          name: docker-credentials
          items:
            - key: .dockerconfigjson
              path: config.json
    
    
"""
        }
    }


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


