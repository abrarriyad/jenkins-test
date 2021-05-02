def GIT_REPO_NAME = params.getOrDefault("gitRepoName", "server-configs")


pipeline {
    agent any
    
    parameters {
        string(defaultValue: GIT_REPO_NAME, description: '', name: 'gitRepoName', trim: true);
    }
    environment {
        gitlabServerConfigUrl = "https://github.com/abrarriyad/${GIT_REPO_NAME}.git"
        // gitlabServerConfigUrl = "https://github.com/abrarriyad/jenkins-test.git"
    }
    stages {
        stage("Checkout") {
            steps {
                git url: "https://github.com/abrarriyad/${GIT_REPO_NAME}.git"
            }
        }

        stage("Run Ansible Playbook") {
            steps {
                ansiblePlaybook colorized: true, installation: 'Ansible', inventory: 'inventory', playbook: 'ansible.yml',tags: "" , skippedTags: ""
            }
        }
    }
}