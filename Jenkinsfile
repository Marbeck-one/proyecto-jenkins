// Jenkinsfile

pipeline {
    agent any // Ejecutar en el agente de Jenkins (que ahora tiene python)

    stages {
        // Etapa 1: Preparar el entorno (Instalar pipenv)
        stage('Install Tools') {
            steps {
                sh 'python3 --version' // Verificar que ahora sí funciona
                sh 'pip install pipenv'  // Instalar pipenv
            }
        }

        // Etapa 2: Instalar Dependencias
        stage('Install Dependencies') {
            steps {
                // pipenv install' usa el requirements.txt
                // y crea un Pipfile y Pipfile.lock
                sh 'pipenv install'
            }
        }

        // Etapa 3: Analizar Seguridad
        stage('Analyze Security') {
            steps {
                echo 'Iniciando análisis de vulnerabilidades...'

                // 'pipenv check' escanea el Pipfile.lock
                // Usamos '|| true' para que el build NO FALLE
                // si encuentra un error (queremos ver el reporte).
                sh 'pipenv check || true'
            }
        }

        // Etapa 4 (Opcional): Pruebas
        stage('Test') {
            steps {
                echo 'Ejecutando pruebas (si las hubiera)...'
            }
        }
    }

    post {
        always {
            echo 'Pipeline finalizado.'
        }
    }
}
