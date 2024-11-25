pipeline {
    agent any
    
    triggers {
        cron('H * * * *')
    }
    
    stages {
        stage('Git Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Hoodini2117/devops-project'
            }
        }
        
        
        stage('Check Disk Usage') {
            steps {
                script {
                    sh '''
                        chmod +x scripttask3.sh
                        ./scripttask3.sh
                    '''
                }
            }
        }
        
        stage('Process Management') {
            steps {
                script {
                    sh '''
                        chmod +x script2.sh
                        ./script2.sh
                    '''
                }
            }
        }
    }
    
    post {
        failure {
            emailext (
                subject: "CRITICAL: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]'",
                body: """
                    FAILED: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]':
                    Check console output at '${env.BUILD_URL}'
                    """,
                to: 'soweirdkai005@gmail.com',
                from: 'jenkins@mail'
            )
        }
    }
}
