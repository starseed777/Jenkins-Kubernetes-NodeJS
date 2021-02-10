pipeline {
    agent any

    stages {
        stage("Building docker image") {
            steps {
                sh "docker build -t . starseed777/nodejs:v1"
            }
        }

    }
}