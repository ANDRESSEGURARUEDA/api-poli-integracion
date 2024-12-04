pipeline {
    agent any
    environment {
        DOCKER_HOST = "tcp://host.docker.internal:2375" // Configuración para Docker Desktop en Windows
    }
    stages {
        stage('Build Maven') {
            steps {
                echo 'Clonando repositorio y ejecutando Maven'
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/ANDRESSEGURARUEDA/api-poli-integracion', credentialsId: 'GitHubToken']]])
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
                    withCredentials([string(credentialsId: 'docker-hub-password', variable: 'DOCKER_PASSWORD')]) {
                        sh '''
                            docker login -u javatechie -p $DOCKER_PASSWORD
                            docker tag repository-app-day:1.0.0.0-SNAPSHOT poli/integration-api-rest
                            docker push poli/integration-api-rest
                        '''
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
    post {
        always {
            echo 'Pipeline finalizado'
        }
        failure {
            echo 'Pipeline fallido'
        }
    }
}
