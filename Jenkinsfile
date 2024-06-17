pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Checkout the repository
                // checkout scm
                git branch: 'master', url: 'https://github.com/nitishdsharma/repo1'
            }
        }
        
        stage('Determine Changed Directories') {
            steps {
                script {
                    // Fetch latest changes
                    sh 'git fetch --all'
                    
                    // Get the list of directories with recent changes under src
                    def changedDirs = sh(
                        script: 'git diff --name-only HEAD~1 -- src/',
                            returnStdout: true
                    ).trim().split('\n')
                    
                    // Print the changed directories for verification
                    echo "Directories with recent changes:"
                    changedDirs.each {
                        echo it
                    }
                    
                    // Set environment variable to pass the list to subsequent stages
                    env.CHANGED_DIRS = changedDirs.join(',')
                }
            }
        }
        
        // Example stage to demonstrate using the CHANGED_DIRS variable
        stage('Build or Deploy Changed Directories') {
            when {
                expression { env.CHANGED_DIRS != '' }
            }
            steps {
                script {
                    // Split the CHANGED_DIRS variable back into a list
                    def changedDirs = env.CHANGED_DIRS.split(',')
                    
                    // Perform actions on each changed directory
                    changedDirs.each { dir ->
                        // Example: Build or deploy each changed directory
                        echo "Building or deploying ${dir}..."
                        // Add your build or deployment steps here
                    }
                }
            }
        }
    }
}
