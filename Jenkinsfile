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
                ansiblePlaybook credentialsId: '33ea877e-dda3-4d92-b3d8-c53dcedfedaf' installation: 'ansible' colorized: true,inventory: '${ansiblePlaybookPath}/inventory',
                playbook: '${ansiblePlaybookPath}/ansible.yml',tags: "" , skippedTags: "",disableHostKeyChecking: true
            }
        }
    }
}
