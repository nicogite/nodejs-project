pipeline {
    agent any

    stages {

        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Building image') {
            steps {
                echo 'Building image....'
                //dockerImage = docker.build my-node-img
                docker build -t my-new-image .
                docker tag my-new-image 127.0.0.1:8084/repository/my-docker-repository/my-new-image
                

            }
        }
        stage('Deploy image') {
            steps {
                echo 'Login into Nexus'
                docker login http://127.0.0.1:8084/repository/my-docker-repository/ --username admin --password admin

                echo 'Push image into Nexus'
                docker push 127.0.0.1:8084/repository/my-docker-repository/my-new-image
            }

        }
    }
}