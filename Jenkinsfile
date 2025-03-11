pipeline {
    agent any

    environment {
        PYTHON_PATH = 'C:\\Users\\Yannick\\AppData\\Local\\Programs\\Python\\Python313\\python.exe'
        SCRIPT_NAME = 'view_machine_data.py'
    }

    triggers {
        pollSCM('* * * * *')  // Revisa cambios cada 5 minutos
    }

    stages {
        stage('Run Python Script') {
            steps {
                bat "\"%PYTHON_PATH%\" %SCRIPT_NAME%"
            }
        }
    }

    post {
        always {
            cleanWs()
        }
    }
}
