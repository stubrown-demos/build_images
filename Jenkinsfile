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
    environment {
        COMMIT_FILES = sh(script: 'git show --pretty="" --name-only', , returnStdout: true).trim()
    }

    stages {
        stage('Process Image') {
            /*when{
        changeset 'images/*'
      }
      */

            steps {
                sh 'echo found "[${COMMIT_FILES}"]'
            }
        }
        stage('Build Image'){
            steps {
                sh 'echo still got "[${COMMIT_FILES}"]'


            }


        }
        stage('Really build image'){
            steps {
                container(name: 'kaniko', shell: '/busybox/sh') {
                    withEnv(['PATH+EXTRA=/busybox']) {
                        sh '''#!/busybox/sh
                    /kaniko/executor --dockerfile images/mvn1_jdk1.docker --destination stuartcbrown/hello-kaniko:latest
                    '''
                    }
                }
            }
        }
    }
}


