#!groovy​

pipeline {
    agent {
        label 'docker'
    }

    options {
        buildDiscarder(logRotator(numToKeepStr:'10'))
        disableConcurrentBuilds()
    }

    stages {
        stage("Up") {
            steps {
                timeout(time:10, unit:'MINUTES') {
                    sh 'docker-compose -p sagdevops-ci-infra run --rm up'
                }
            }
        }
        stage("Test") {
            steps {
                timeout(time:5, unit:'MINUTES') {
                    sh 'docker-compose -p sagdevops-ci-infra run --rm test'
                }
            }
            post {
                //always {
                //    sh 'docker-compose -p sagdevops-ci-infra stop'
                //}
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
