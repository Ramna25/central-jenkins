pipeline {
    agent any


    stages {
        stage('Start'){
            steps{
                script{
                def branchname = GIT_BRANCH
                def gitrepo = scm.getUserRemoteConfigs()[0].getUrl()
                def reponame= scm.getUserRemoteConfigs()[0].getUrl().tokenize('/').last().split("\\.")[0]
                def tag= sh(returnStdout: true, script: "git tag --contains | head -1").trim()

                echo "Branch Name: ${branchname}"
                    echo "Git Repository URL: ${gitrepo}"
                    echo "Repository Name: ${reponame}"
                    echo "Tag Name: ${tag}"

                   
                

                build job: 'input', wait: false, parameters: [string(name: 'branchname', value: branchname ),string(name: 'reponame', value: reponame ), string(name: 'gitrepo', value: gitrepo )] 
                

                }
            }
        }
    }
}
