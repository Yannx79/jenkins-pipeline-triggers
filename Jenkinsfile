pipeline {
    agent any
    // Check for changes in the SCM every minute
   triggers {
       pollSCM '* * * * *'
    }
    
    stages {
        stage('Run Python Script') {
            steps {
                bat 'python view_machine_data.py'
            }
        }
    }
    
    post {
        always {
            cleanWs()
        }
    }
}
