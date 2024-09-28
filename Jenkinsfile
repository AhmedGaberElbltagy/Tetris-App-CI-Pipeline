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
                    withCredentials([usernamePassword(credentialsId: 'github', usernameVariable: 'GITHUB_USER', passwordVariable: 'GITHUB_TOKEN')]) {
                    
                    git branch: 'main', url: 'https://github.com/AhmedGaberElbltagy/Tetris-App-Manifest-files.git'
                    sh '''
                        echo $GITHUB_USER' 
                        echo $GITHUB_TOKEN' 
                        git config user.email "ahmedelbltagy1999@gmail.com" 
                        git config user.name "AhmedGaberElbltagy"     
                         ls -l      
                        sed -n '/image/p' K8S/deployment.yaml

                        
                    '''

                }

                        // git add java-maven-sonar-argocd-helm-k8s/spring-boot-app-manifests/deployment.yml
                        // git commit -m "Update deployment image to version ${BUILD_NUMBER}"
                        // git push https://${GITHUB_TOKEN}@github.com/${GIT_USER_NAME}/${GIT_REPO_NAME} HEAD:main
            }
        }
    }
}
    