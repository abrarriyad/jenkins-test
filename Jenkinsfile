def GIT_REPO_NAME = params.getOrDefault("gitRepoName", "server-configs")


pipeline {
    agent any
    
    parameters {
        string(defaultValue: GIT_REPO_NAME, description: '', name: 'gitRepoName', trim: true);
    }
    environment {
        githubRepoUrl = "https://github.com/abrarriyad/${GIT_REPO_NAME}.git"
        ansiblePlaybookPath = "/var/lib/jenkins/workspace/jenkins_test"
    }
    stages {
        stage("Checkout") {
            steps {
                git url: "https://github.com/abrarriyad/${GIT_REPO_NAME}.git"
            }
        }

        stage("Run Ansible Playbook") {
            steps {
                ansiblePlaybook colorized: true, installation: 'Ansible', inventory: '${ansiblePlaybookPath}/inventory',
                playbook: '${ansiblePlaybookPath}/ansible.yml',tags: "" , skippedTags: "",disableHostKeyChecking: true
            }
        }
    }
}
