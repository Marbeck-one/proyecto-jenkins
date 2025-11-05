// Jenkinsfile

pipeline {
    agent any 

    stages {
        // Etapa 1: Verificar que las herramientas están instaladas
        stage('Verify Tools') {
            steps {
                sh 'python3 --version' 
                sh 'pipenv --version'  // Verificamos que pipenv existe
            }
        }

        // Etapa 2: Instalar Dependencias del Proyecto
        stage('Install Dependencies') {
            steps {
                sh 'pipenv install'
            }
        }

        // Etapa 3: Analizar Seguridad
        stage('Analyze Security') {
            steps {
                echo 'Iniciando análisis de vulnerabilidades...'
                // 'pipenv check' escanea el entorno
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
