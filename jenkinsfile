pipeline {
    agent {
        label 'docker'
    }

    stages {
        stage('Build Docker Image') {
            steps {
                script {
                    sh 'docker build -t paulaadel11/docker-react -f dockerfile.dev .'
                }
            }
        }

        stage('Run Tests') {
            steps {
                script {
                    env.DOCKER_BUILDKIT = 1
                    sh 'docker run -e CI=true paulaadel11/docker-react npm test'
                }
            }
        }
    }
}