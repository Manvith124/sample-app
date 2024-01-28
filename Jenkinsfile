pipeline {
    agent any
    tools {
     maven 'maven'
    }
    stages {
        stage('git clone') {
            steps {
                git branch: 'main', url: 'https://github.com/Manvith124/webapplication.git'
            }
        }
        stage('maven') {
            steps {
                sh 'mvn clean install'
            }
        }
        stage('docker image build') {
            steps {
                sh 'docker build -t shivakumarveerapur124/app2 .'
            }
        }
        stage('docker image push'){
            steps {
               withCredentials([string(credentialsId: 'pass', variable: 'dockpassword')]) {
                    sh 'docker login -u shivakumarveerapur124 -p ${dockpassword}'
                
                }
               
                sh 'docker push shivakumarveerapur124/app2'
            }
        }
    }
}
