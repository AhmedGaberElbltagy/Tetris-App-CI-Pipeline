pipeline {
    agent any

    tools{
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
                    
                    def newImage = "my-spring-boot-app:${env.BUILD_NUMBER}"
                    sh 'echo ${env.BUILD_NUMBER}'
                    withCredentials([usernamePassword(credentialsId: 'github', usernameVariable: 'GITHUB_USER', passwordVariable: 'GITHUB_TOKEN')]) {
                    
                    git branch: 'main', url: 'https://github.com/AhmedGaberElbltagy/Tetris-App-Manifest-files.git'
                    sh '''
                        echo $GITHUB_USER' 
                        echo $GITHUB_TOKEN' 
                        git config user.email "ahmedelbltagy1999@gmail.com" 
                        git config user.name "AhmedGaberElbltagy"     
                        
                        sed -i 's|image: .*|image: ${newImage}|' K8S/deployment.yaml
                        

                        
                    '''
                }

                }
            }
        }
    }
}
    