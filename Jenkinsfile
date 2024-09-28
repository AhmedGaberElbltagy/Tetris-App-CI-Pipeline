pipeline {
    agent any
    environment{
       
    }
    tools{
        gradle '8.10'
    }
    stages {
    //     stage('Cleanup Workspace') {
    //         steps {
    //             cleanWs()
    //         }
    //     }
    // }
    //     stage('Checkout') {
    //         steps {
    //             checkout scm
    //         }
    //     }       
    //     stage('Lint') {
    //         steps {
    //             script {
    //               // Run the gradle check task, which includes linting
    //                 //LintApp functions is avaliable in the jenkins-shared-library
    //                 lintApp()
    //             }
    //         }
        
    //         post {
    //             always {
    //                 // Archive the linting report if any
    //                 archiveArtifacts artifacts: '**/build/reports/**', allowEmptyArchive: true
    //             }
    //         }
    //     }
    //     stage('Test') {
    //         steps {
    //             script {
    //                 //testApp functions is avaliable in the jenkins-shared-library
    //                 testApp()
    //             }
    //         }
    //     }
    //     stage('Build') {
    //         steps {
    //             script {
    //                 //buildJar functions is avaliable in the jenkins-shared-library
    //                 buildJar()
    //             }
    //         }
    //     }
    //     stage('Package') {
    //         steps {
    //             script {
    //                 //packageApp functions is avaliable in the jenkins-shared-library
    //                 packageApp()
    //             }
    //         }
    //     }
    //     stage('Build and Push Image '){
    //         steps {
    //             script {
    //                  //buildImage , pushImage functions is avaliable in the jenkins-shared-library,
    //                  // and they takes a varaiable 'image name'
    //                  buildImage 'my-spring-boot-app:v3'
    //                  dockerLogin()
    //                  pushImage 'my-spring-boot-app:v3'
    //             }
    //         }
    //     }
         stage('Update Deployment File') {
            environment {
                GIT_USER_NAME = "MohamedMagdy840"
            }
            steps {
                script {
                    withCredentials([string(credentialsId: 'git-token', variable: 'GITHUB_TOKEN')]) {
                        sh '''
                            # Update the local deployment file
                            git config user.email "jenkins@gmail.com"
                            git config user.name "jenkins"
                            sed -i 's|image: .*|image: mohamedmagdy840/tetris:latest|' deployment-service.yaml
                            
                            # Pull latest changes from the remote repository
                            git pull origin main

                            # Configure Git remote to use credentials for pushing
                            git remote set-url origin https://MohamedMagdy840:$GITHUB_TOKEN@github.com/MohamedMagdy840/tetris-deployment-file.git
                            git add deployment-service.yaml
                            git commit -m 'Update deployment image to version mohamedmagdy840/tetris:latest'
                            git push origin HEAD:main

                        '''
                    }
                }
            }
         }
    }
}
    