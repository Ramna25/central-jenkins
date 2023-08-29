pipeline {
    agent any


    stages {
        stage('Start'){
            steps{
                script{
                def branchname = GIT_BRANCH
                def gitrepo = scm.getUserRemoteConfigs()[0].getUrl()
                def reponame= scm.getUserRemoteConfigs()[0].getUrl().tokenize('/').last().split("\\.")[0]

                echo "Branch Name: ${branchname}"
                    echo "Git Repository URL: ${gitrepo}"
                    echo "Repository Name: ${reponame}"

                    // Trigger the release script using the sh step
                    sh "path/to/your/release/script.sh ${branchname} ${gitrepo} ${reponame}"
                

               // build job: 'sandboxserver', wait: false, parameters: [string(name: 'branchname', value: branchname ),string(name: 'reponame', value: reponame ), string(name: 'gitrepo', value: gitrepo )] 
                

                }
            }
        }
    }
}
