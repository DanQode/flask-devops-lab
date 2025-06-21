pipeline {
    agent any

    stages {
        stage('Levantar entorno') {
            steps {
                echo 'Ejecutando docker-compose up...'
                sh 'docker-compose up -d'
            }
        }

        stage('Verificar app') {
            steps {
                echo 'Validando salud de la aplicación Flask...'
                sh 'curl -f http://localhost:5000/health'
            }
        }

        stage('Finalizado') {
            steps {
                echo 'Pipeline completado correctamente 🎉'
            }
        }
    }
}
