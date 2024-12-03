pipeline {
    agent any
    stages {
        stage('Build Maven') {
            steps {
                echo 'Clonando repositorio y ejecutando Maven'
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/ANDRESSEGURARUEDA/api-poli-integracion']]])
                sh 'mvn clean package'
                sh 'mvn clean install'
            }
        }
        stage('Build Docker Image') {
            steps {
                echo 'Construyendo la imagen de Docker'
                script {
                    sh 'docker build -t repository-app-day:1.0.0.0-SNAPSHOT .'
                }
            }
        }
        stage('Push Image to Hub') {
            steps {
                echo 'Subiendo la imagen al Docker Hub'
                script {
                    withCredentials([string(credentialsId: '123456', variable: 'DOCKER_PASSWORD')]) {
                        sh 'docker login -u javatechie -p $DOCKER_PASSWORD'
                        sh 'docker push poli/integration-api-rest'
                    }
                }
            }
        }
        stage('Execute Commands') {
            steps {
                echo 'Ejecutando comandos del script comandos.sh'
                script {
                    sh './comandos.sh'
                }
            }
        }
    }
}
