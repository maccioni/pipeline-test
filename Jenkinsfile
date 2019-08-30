pipeline {
    agent any

    stages {
        stage('Download code from GitHub') {
            steps {
                echo "Downloading code from https://github.com/maccioni/forward-cicd-ansible"
                echo "currentBuild.currentResult: ${currentBuild.currentResult}"
            }
        }
        stage('Pre-change validation') {
            steps {
                sh "echo 'Placeholder for Pre-change validation'"
                echo "currentBuild.currentResult: ${currentBuild.currentResult}"
            }
        }
        stage('Simulate change in Sandbox') {
            steps {
                sh "echo 'Placeholder for policy simulation on Forward Sandbox'"
                echo "currentBuild.currentResult: ${currentBuild.currentResult}"
            }
        }
        stage('Apply network change') {
            when {
                expression { ${currentBuild.currentResult} == 'SUCESS' }
            }
            steps {
                sh "echo 'Placeholder for Apply network change'"
                echo "currentBuild.currentResult: ${currentBuild.currentResult}"
            }
        }
        stage('Post-change validation') {
            steps {
                script {
                    try {
                        sh "echo 'Placeholder for Post-change validation'"
                        echo "currentBuild.currentResult: ${currentBuild.currentResult}"
                    } catch (error) {
                        error("Changes failed testing.  Rolled back.")
                        echo "currentBuild.currentResult: ${currentBuild.currentResult}"
                    }
                }
            }
        }
    }
    post {
      always {
        script {
          echo "Post section: run always"
          echo "currentBuild.currentResult: ${currentBuild.currentResult}"
          echo "currentBuild.Result: ${currentBuild.result}"
        }
      }
      failure {
        script {
          echo "Post section: run on failure only"
          currentBuild.result = "FAILURE"
        }
      }
    }
}
