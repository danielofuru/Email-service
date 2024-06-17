pipeline {
    agent any
    
    environment {
        // Define the recipients as an environment variable for ease of reuse
        RECIPIENTS = 'danielofurutech@gmail.com, goodnessm508@gmail.com.com, guddytechs@gmail.com, estheronyinye011@gmail.com'
    }
    
    stages {
        stage('Build') {
            steps {
                // Your build steps go here
                echo 'Building...'
            }
        }
        
        stage('Test') {
            steps {
                // Your test steps go here
                echo 'Testing...'
            }
        }
        
        stage('Deploy') {
            steps {
                // Your deploy steps go here
                echo 'Deploying...'
            }
        }
    }
    
    post {
        always {
            script {
                // Determine the build status and send an email accordingly
                def buildStatus = currentBuild.currentResult
                emailext(
                    to: "${env.RECIPIENTS}",
                    subject: "${buildStatus}: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]'",
                    body: """<p>Build Status: ${buildStatus}</p>
                             <p>You can check the build details at: <a href="${env.BUILD_URL}">${env.BUILD_URL}</a></p>"""
                    <p>This is a project from the Dev-Sec-Ops team, and i am glad it was successful Thanks</p>
                )
            }
        }
        
        success {
            echo 'Build was successful!'
        }
        
        failure {
            echo 'Build failed!'
        }
        
        unstable {
            echo 'Build is unstable!'
        }
        
        changed {
            echo 'Build result has changed!'
        }
    }
}
