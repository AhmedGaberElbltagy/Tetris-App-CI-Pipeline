pipeline {
    agent any
    environment{
       
    }
    tools{
        gradle '8.10'
    }
    stages {
        stage('Update Deployment File') {
            environment {
                GIT_REPO_NAME = "Tetris-App-Manifest-files" 
                GIT_USER_NAME = "AhmedGaberElbltagy"   
            }
            steps {
                withCredentials([string(credentialsId: 'github_token', variable: 'GITHUB_TOKEN')]) {
                    sh '''
                        git config user.email "ahmedelbltagy1999@gmail.com" 
                        git config user.name "AhmedGaberElbltagy"           
                        sed -n '/image/p' deployment-service.yaml

                        
                    '''
                }
                        // git add java-maven-sonar-argocd-helm-k8s/spring-boot-app-manifests/deployment.yml
                        // git commit -m "Update deployment image to version ${BUILD_NUMBER}"
                        // git push https://${GITHUB_TOKEN}@github.com/${GIT_USER_NAME}/${GIT_REPO_NAME} HEAD:main
            }
        }
    }
}
    