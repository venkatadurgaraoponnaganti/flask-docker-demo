pipeline {
    agent any

    stages {

        stage('Pull from GitHub') {
            steps {
                echo 'Cloning repository from GitHub...'
                git branch: 'main',
                    url: 'https://github.com/venkatadurgaraoponnaganti/flask-docker-demo.git'
            }
        }

        stage('Build') {
            steps {
                echo 'Installing dependencies...'
                sh '''
                    pip install --n0-cache-dir -r requirements.txt
                '''
            }
        }

        stage('Deploy') {
            steps {
                echo 'Building Docker image...'
                sh '''
                    docker build -t flask-docker-demo .
                '''
            }
        }

        stage('Run on EC2') {
            steps {
                echo 'Running container on port 5000...'
                sh '''
                    docker run -d -p 5000:5000 flask-docker-demo
                '''
            }
        }
    }
}

