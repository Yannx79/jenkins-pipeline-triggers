pipeline {
    agent any
    // Check for changes in the SCM every minute
   triggers {
       pollSCM '* * * * *'
    }
    
    stages {
        stage('Run Python Script') {
            steps {
                bat 'C:\Users\Yannick\AppData\Local\Programs\Python\Python313\python.exe view_machine_data.py'
            }
        }
    }
    
    post {
        always {
            cleanWs()
        }
    }
}
