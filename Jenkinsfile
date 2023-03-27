node {
    def app

    stage('Clone repository') {
        checkout scm
    }

    stage('Update GIT') {
            script {
                catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
                    withCredentials([usernamePassword(credentialsId: 'github', passwordVariable: 'GIT_PASSWORD', usernameVariable: 'GIT_USERNAME')]) {
                        //def encodedPassword = URLEncoder.encode("$GIT_PASSWORD",'UTF-8')
                        sh "git config user.email thush1990@gmail.com"
                        sh "git config user.name thush1990"
                        //sh "git switch master"
                        sh "cat frontend.yaml"
                        sh "sed -i 's+thush1990/demo-ci.*+thush1990/demo-ci:${DOCKERTAG}+g' frontend.yaml"
                        sh "cat frontend.yaml"
                        sh "git add ."
                        sh "git commit -m 'Done by Jenkins Job changemanifest: ${env.BUILD_NUMBER}'"
                        sh "git push https://${GIT_USERNAME}:${GIT_PASSWORD}@github.com/${GIT_USERNAME}/demo-cd.git HEAD:main"
      }
    }
  }
}
}
