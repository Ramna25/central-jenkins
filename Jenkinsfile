pipeline {
    agent any

    stages {
        stage('Start') {
            steps {
                script {
                    def branchname = GIT_BRANCH
                    def gitrepo = scm.getUserRemoteConfigs()[0].getUrl()
                    def reponame = scm.getUserRemoteConfigs()[0].getUrl().tokenize('/').last().split("\\.")[0]

                    // Create a GitHub tag
                    sh "git tag -a ${branchname} -m 'Tagging release ${branchname}'"
                    sh "git push origin ${branchname}"

                    // Create a GitHub release using GitHub API
                    def githubToken = 'your_github_token_here'
                    def apiUrl = "https://api.github.com/repos/${reponame}/releases"
                    def releaseName = "Release ${branchname}"
                    def releaseBody = "This is the release for branch ${branchname}"
                    def releaseTag = "${branchname}"

                    def createRelease = """
                    curl -X POST -H "Authorization: token ${mytoken}" -d '{
                        "tag_name": "${releaseTag}",
                        "target_commitish": "${branchname}",
                        "name": "${releaseName}",
                        "body": "${releaseBody}",
                        "draft": false,
                        "prerelease": false
                    }' "${apiUrl}"
                    """

                    sh createRelease

                    // Trigger the sandboxserver job
                    build job: 'sandboxserver', wait: false, parameters: [
                        string(name: 'branchname', value: branchname),
                        string(name: 'reponame', value: reponame),
                        string(name: 'gitrepo', value: gitrepo)
                    ]
                }
            }
        }
    }
}
