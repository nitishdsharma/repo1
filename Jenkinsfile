// pipeline {
//     agent any

//     stages {
//         stage('Checkout') {
//             steps {
//                 // Checkout the repository
//                 git branch: 'master', url: 'https://github.com/nitishdsharma/repo1'
//             }
//         }
        
//         stage('Determine Changed Subdirectories') {
//             steps {
//                 script {
//                     // Fetch latest changes
//                     sh 'git fetch --all'
                    
//                     // Get the list of subdirectories under src that have recent changes
//                     def changedDirs = sh(
//                         script: '''
//                             git diff --name-only HEAD~1 -- src/ |
//                             grep '^src/[^/]*' | 
//                             cut -d '/' -f 2 | 
//                             sort -u
//                         ''',
//                         returnStdout: true
//                     ).trim().split('\n')
                    
//                     // Print the changed subdirectories for verification
//                     echo "Subdirectories with recent changes under src:"
//                     changedDirs.each {
//                         echo it
//                     }
                    
//                     // Set environment variable to pass the list to subsequent stages
//                     env.CHANGED_SUBDIRS = changedDirs.join(',')
//                 }
//             }
//         }
        
//         // Example stage to demonstrate using the CHANGED_SUBDIRS variable
//         // stage('Build or Deploy Changed Subdirectories') {
//         //     when {
//         //         expression { env.CHANGED_SUBDIRS != '' }
//         //     }
//         //     steps {
//         //         script {
//         //             // Split the CHANGED_SUBDIRS variable back into a list
//         //             def changedSubdirs = env.CHANGED_SUBDIRS.split(',')
                    
//         //             // Perform actions on each changed subdirectory
//         //             changedSubdirs.each { subdir ->
//         //                 // Example: Build or deploy each changed subdirectory
//         //                 echo "Building or deploying ${subdir}..."
//         //                 // Add your build or deployment steps here
//         //             }
//         //         }
//         //     }
//         // }
//     }
// }
