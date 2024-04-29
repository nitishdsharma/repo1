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
                    def currentCommit = sh(script: "git rev-parse HEAD", returnStdout: true).trim()
                    def previousCommit = sh(script: "git rev-parse HEAD^", returnStdout: true).trim()
                    // def diffOutput = sh(script: "git diff origin/master ${srcDir}", returnStdout: true).trim()
                    def diffOutput = sh(script: "git diff ${previousCommit} ${currentCommit} -- ${srcDir}", returnStdout: true).trim()
                    // Check if there are differences
                    if (diffOutput) {
                        echo "Changes detected in ${srcDir} between ${previousCommit} and ${currentCommit}:"
                        echo "${diffOutput}"
                    } else {
                        echo "No changes detected in ${srcDir}"
                    }
                }
                }
            }
        }
      }
