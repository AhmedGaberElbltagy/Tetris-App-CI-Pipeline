pipeline {
    agent any

    tools {
        gradle 'gradle'
    }
    stages {
        stage('Update Deployment File') {
            environment {
                GIT_REPO_NAME = "Tetris-App-Manifest-files" 
                GIT_USER_NAME = "AhmedGaberElbltagy"   
            }
            steps {
                script {
                    def newImage = "ahmedelbltagy/my-spring-boot-app:${env.BUILD_NUMBER}"
                    sh "echo ${env.BUILD_NUMBER}"
                    
                    withCredentials([usernamePassword(credentialsId: 'github', usernameVariable: 'GITHUB_USER', passwordVariable: 'GITHUB_TOKEN')]) {
                        git branch: 'main', url: "https://github.com/${GIT_USER_NAME}/${GIT_REPO_NAME}.git"
                        sh """
                            echo $GITHUB_USER
                            echo $GITHUB_TOKEN
                            git config user.email "ahmedelbltagy1999@gmail.com"
                            git config user.name "AhmedGaberElbltagy"
                            
                            # Use double quotes to allow variable substitution
                            sed -i "s|image: .*|image: ${newImage}|" K8S/deployment.yaml


                             git pull origin main

                            # Configure Git remote to use credentials for pushing
                            git remote set-url origin $GITHUB_TOKEN@github.com:AhmedGaberElbltagy/Tetris-App-Manifest-files.git
                            git add K8S/deployment.yaml
                            git commit -m 'Update deployment image to version ${env.BUILD_NUMBER} '
                            git push origin HEAD:main
                        """
                    }
                }
            }
        }
    }
}
