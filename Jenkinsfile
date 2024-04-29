pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
              git branch: 'master', url: 'https://github.com/nitishdsharma/repo1'
            }
        }

        stage('Terraform Init') {
            steps {
                // Initialize Terraform
                script {
                    def changedFiles = sh(script: "git diff --name-only HEAD^ HEAD -- src/", returnStdout: true).trim()
                    def shouldDeploy = changedFiles != ''

                    if (shouldDeploy) {
                        sh "ls src"
                    } else {
                        echo "No changes detected in src directory. Skipping Terraform plan."
                    }
                }
                }
            }
        }
      }
