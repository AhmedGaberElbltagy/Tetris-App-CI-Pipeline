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
                    sh '''
                        echo $GITHUB_USER' 
                        echo $GITHUB_TOKEN' 
                        git config user.email "ahmedelbltagy1999@gmail.com" 
                        git config user.name "AhmedGaberElbltagy"           
                        sed -n '/image/p' deployment-service.yaml

                        
                    '''
                    withCredentials([usernamePassword(credentialsId: 'github', usernameVariable: 'GITHUB_USER', passwordVariable: 'GITHUB_TOKEN')]) {
                     // Your commands here
                    sh 'echo $GITHUB_USER'
                    sh 'echo $GITHUB_TOKEN'
}

                }

                        // git add java-maven-sonar-argocd-helm-k8s/spring-boot-app-manifests/deployment.yml
                        // git commit -m "Update deployment image to version ${BUILD_NUMBER}"
                        // git push https://${GITHUB_TOKEN}@github.com/${GIT_USER_NAME}/${GIT_REPO_NAME} HEAD:main
            }
        }
    }
}
    