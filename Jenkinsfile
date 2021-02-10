pipeline {
    agent any
    environment {
        DOCKER_TAG = DockerTag()
    }

    stages {
        stage("Building docker image") {
            steps {
                sh "docker build . -t starseed777/nodejs:${DOCKER_TAG}"
            }
        }

    }
}

def DockerTag() {
    def tag = sh script: "git rev-parse HEAD", returnStdout: true
    return tag 
}