#!groovy
properties([disableConcurrentBuilds()])

pipeline{
    agent none
    options {
        buildDiscarder(logRotator(numToKeepStr: '3', artifactNumToKeepStr: '3'))
        timestamps()
    }
    triggers {pollSCM('* * * * *') }
    stages{
        stage("Build frontend and backend"){
            agent {
                docker {
                    image 'node:10.15.3-alpine'
                }
            }
            steps{
                git 'https://github.com/EricRoux/docker-mern'
                dir("frontend-docker") {
                    echo " ============== Build frontend =================="
                    sh 'npm i'
                    sh 'npm run build'
                }
                dir("backend-docker") {
                    echo " ============== Build backend ==================="
                    sh 'npm i'
                    sh 'npm run build'
                }
                stash includes: '**/build/', name: 'build' 
            }
        }
        stage("Build all progect"){
            agent any
            steps{
                echo " ============== Build backend ==================="
                git 'https://github.com/EricRoux/docker-mern'
                unstash 'build'
                sh 'docker-compose build'
            }
        }
    }
}