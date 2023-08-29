pipeline {
    agent any

    stages {
        stage('Start') {
            steps {
                script {
                    def branchname = GIT_BRANCH
                    def gitrepo = scm.getUserRemoteConfigs()[0].getUrl()
                    def reponame = scm.getUserRemoteConfigs()[0].getUrl().tokenize('/').last().split("\\.")[0]

                    echo "Branch Name: ${branchname}"
                    echo "Git Repository URL: ${gitrepo}"
                    echo "Repository Name: ${reponame}"

                    // Get the latest tag using the sh step
                    def repotag = sh(script: 'git describe --tags $(git rev-list --tags --max-count=1)', returnStdout: true).trim()
                    echo "Latest Tag: ${repotag}"
                }
            }
        }
    }
}

                   
                

              //  build job: 'input', wait: false, parameters: [string(name: 'branchname', value: branchname ),string(name: 'reponame', value: reponame ), string(name: 'gitrepo', value: gitrepo )] 
                

                }
            }
        }
    }
}
