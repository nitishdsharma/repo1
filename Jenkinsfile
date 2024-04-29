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
                script {
                    def srcDir = 'src'
                    def diffOutput = sh(script: "git diff origin/master ${srcDir}", returnStdout: true).trim()
                    // Check if there are differences
                    if (diffOutput) {
                        echo "Changes detected in ${srcDir}:"
                        echo "${diffOutput}"
                    } else {
                        echo "No changes detected in ${srcDir}"
                    }
                }
                }
            }
        }
      }
