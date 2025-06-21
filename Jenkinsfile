pipeline {
    agent any

    stages {
        stage('Levantar entorno') {
            steps {
                echo 'Ejecutando docker compose up...'
                sh 'docker compose up -d'
            }
        }

        stage('Verificar app') {
            steps {
                echo 'Esperando a que Flask esté listo...'
                sh '''
                    for i in {1..10}; do
                        curl -fs http://localhost:5000/health && break
                        echo "Intento $i fallido, esperando 3 segundos..."
                        sleep 3
                    done
                '''
            }
        }

        stage('Finalizado') {
            steps {
                echo 'Pipeline completado correctamente'
            }
        }
    }
}
