pipeline {
 /*   agent {
        docker {
            image 'node:6-alpine'
            args '-p 3000:3000 -p 5000:5000' 
        }
    }*/
    agent {
        kubernetes {
            yaml '''
                apiVersion: v1
                kind: Pod
                metadata:
                    labels:
                        app: node
                spec:
                    containers:
                    - name: node
                      image: node:6-alpine
                      ports:
                      - containerPort: 3000 
                      - containerPort: 5000
                      tty: true
                '''
        }
    }
    environment {
        CI = 'true'
    }
    stages {
        stage('Build') {
            steps {
                container('node') {
                    sh 'npm install'
                }
            }
        }
        stage('Test') {
            steps {
                container('node') {
                    sh './jenkins/scripts/test.sh'
                }
            }
        }
    }
}