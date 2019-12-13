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
        //IMG_TO_BUILD = "${COMMIT_FILES}"
        DOCKER_DEST = "stushq"
    }

    stages {

        stage('Building docker image'){
            //when{
            //    changeset 'images/*'
            //}

            environment{

              IMG_NAME = sh(script: 'basename "${IMG_TO_BUILD}"', , returnStdout: true).trim()
            }
            steps {
                script{
                    INDID = COMMIT_FILES.split("")
                }
                container(name: 'kaniko', shell: '/busybox/sh') {
                    withEnv(['PATH+EXTRA=/busybox']) {
                        echo "building image [${INDID}] to [${DOCKER_DEST}/${INDID}]"
                        sh 'sleep 5'
                        //sh '''#!/busybox/sh
                 //   /kaniko/executor --dockerfile images/${IMG_NAME} --destination ${DOCKER_DEST}/${IMG_NAME}:latest
                //    '''
                    }
                }
            }
        }
    }
}



