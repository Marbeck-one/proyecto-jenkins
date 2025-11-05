// Jenkinsfile

pipeline {
    agent any // Ejecutar en cualquier agente disponible

    stages {
        // Etapa 1: Preparar el entorno (Instalar Python y pipenv)
        stage('Install Tools') {
            steps {
                sh 'python3 --version'
                sh 'apt-get update && apt-get install -y python3-pip'
                sh 'pip install pipenv'
            }
        }

        // Etapa 2: Instalar Dependencias (de forma segura)
        stage('Install Dependencies') {
            steps {
                // Instala las dependencias del Pipfile (si no existe, usa requirements)
                sh 'pipenv install --skip-lock'
            }
        }
        
        // Etapa 3: Analizar Seguridad
        stage('Analyze Security') {
            steps {
                echo 'Iniciando análisis de vulnerabilidades...'
                
                // 'pipenv check' escanea el entorno en busca de
                // vulnerabilidades conocidas en las dependencias.
                // Usamos '|| true' para que el pipeline no falle
                // si encuentra vulnerabilidades (queremos ver el reporte).
                sh 'pipenv check || true'
            }
        }
        
        // Etapa 4 (Opcional): Pruebas y Construcción
        stage('Test & Build') {
            steps {
                echo 'Ejecutando pruebas (si las hubiera)...'
                // Aquí irían tus comandos de prueba, ej: sh 'python3 -m pytest'
            }
        }
    }
    
    // Acciones que se ejecutan al final (falle o no)
    post {
        always {
            echo 'Pipeline finalizado.'
        }
    }
}
