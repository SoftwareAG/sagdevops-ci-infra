#!groovy​

pipeline {
    agent none

    options {
        buildDiscarder(logRotator(numToKeepStr:'10'))
        disableConcurrentBuilds()
    }

    stages {
        stage("Prepare") {
            agent {
                label 'master'
            }
            steps {
                checkout scm
                sh 'git submodule update --init' 
                stash(name:'scripts', includes:'**')
            }
        }

        stage("Up and Test") {
            agent {
                label 'w64' // this is Windows pipeline
            }
            tools {
                ant "ant-1.9.7"
                jdk "jdk-1.8"
            }
            steps {
                unstash 'scripts'
                timeout(time:20, unit:'MINUTES') {
                    bat 'ant up test'
                }
            }
            post {
                success {
                    junit 'build/tests/**/TEST-*.xml'
                }
                unstable {
                    junit 'build/tests/**/TEST-*.xml'
                }
            }
        }
    }
}

