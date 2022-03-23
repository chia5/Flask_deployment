node('Ubuntu'){
    
    stage('Clone repository') {
        
        git branch: 'main', url: 'https://github.com/chia5/Flask_deployment.git'
        
    }

    stage('Update GIT') {
            script {
                catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
                    withCredentials([usernamePassword(credentialsId: 'Github', passwordVariable: 'GIT_PASSWORD', usernameVariable: 'GIT_USERNAME')]) {
                        //def encodedPassword = URLEncoder.encode("$GIT_PASSWORD",'UTF-8')
                        sh "git config user.email chi@example.com"
                        sh "git config user.name Chika"
                        //sh "git switch main"
                        sh "cat deployment.yaml"
                        sh "sed -i 's+chash07/helloapp.*+chash07/helloapp:${DOCKERTAG}+g' deployment.yaml"
                        sh "cat deployment.yaml"
                        sh "git add ."
                        sh "git commit -m 'Done by Jenkins Job changemanifest: ${env.BUILD_NUMBER}'"
                        sh "git push https://${GIT_USERNAME}:${GIT_PASSWORD}@github.com/${GIT_USERNAME}/Flask_deployment.git HEAD:main"
      }
    }
  }
}
}
