pipeline {
    agent any

    environment {
        PYTHON_PATH = 'C:\\Users\\Yannick\\AppData\\Local\\Programs\\Python\\Python313\\python.exe'
        SCRIPT_NAME = 'view_machine_data.py'
        LOG_FILE = 'script_output.log'
    }

    triggers {
        pollSCM('H/5 * * * *')  // Revisa cambios cada 5 minutos
    }

    stages {
        stage('Verify Python Version') {
            steps {
                bat "\"%PYTHON_PATH%\" --version"
            }
        }

        stage('Run Python Script') {
            steps {
                script {
                    try {
                        bat "\"%PYTHON_PATH%\" %SCRIPT_NAME% > %LOG_FILE% 2>&1"
                    } catch (Exception e) {
                        echo "Error al ejecutar el script: ${e}"
                        error "Fallo en la ejecución de Python"
                    }
                }
            }
        }

        stage('Save Logs') {
            steps {
                archiveArtifacts artifacts: 'script_output.log', fingerprint: true
            }
        }
    }

    post {
        success {
            echo "Ejecución completada con éxito ✅"
        }
        failure {
            echo "Hubo un error en la ejecución ❌"
        }
        always {
            cleanWs()
        }
    }
}
