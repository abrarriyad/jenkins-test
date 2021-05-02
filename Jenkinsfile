def GIT_REPO_NAME = params.getOrDefault("gitRepoName", "server-configs")


pipeline {
    agent any
    
    parameters {
        string(defaultValue: GIT_REPO_NAME, description: '', name: 'gitRepoName', trim: true);
    }
    environment {
       
        gitlabServerConfigUrl = "ssh://git@github.com:abrarriyad:221/${GIT_REPO_NAME}.git"
    }
    stages {
        stage("Checkout") {
            steps {
                git url: ${env.gitlabServerConfigUrl}
            }
        }
    }
}