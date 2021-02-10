pipeline {
    agent any
    environment {
        DOCKER_TAG = DockerTag()
        registry = "starseed777/nodejs"
        registryCredential = "dockerhub"

    }

    stages {
        stage("Building docker image") {
            steps {
                sh "docker build . -t starseed777/nodejs:${DOCKER_TAG}"
            }
        }

        stage("Push built image to dockerhub") {
            steps {
                script{
                   docker.withRegistry("",registryCredential) {
                    sh "docker push starseed777/nodejs:$DOCKER_TAG"
                   } 
                }
            }
        }
        stage("Deploy to k8s") {
            steps {
                sh "chmod +x changeTag.sh"

                sh "./changeTag.sh $DOCKER_TAG"
            }
        }

    }
}

def DockerTag() {
    def tag = sh script: "git rev-parse HEAD", returnStdout: true
    return tag 
}