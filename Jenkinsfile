pipeline {
    agent any

    stages {
        stage('Download code from GitHub') {
            steps {
                echo "Downloading code from https://github.com/maccioni/forward-cicd-ansible"
                echo "currentBuild.currentResult: ${currentBuild.currentResult}"
                slackSend(channel: 'demo-notifications', message: 'new test message from jenkins', username: 'fabriziomaccioni', token: 'GnbPV5e2SVkTkyMiRXaCFEXK', teamDomain: 'fwd-net')
            }
        }
        stage('copied from test') {
            steps {
                echo 'Check enviroment '
                sh 'whoami'
                sh 'who am i'
                sh 'ls -l'
                sh 'env'
                slackSend(channel: 'demo-notifications', message: 'test message from jenkins', username: 'fabriziomaccioni', token: 'GnbPV5e2SVkTkyMiRXaCFEXK', teamDomain: 'fwd-net')
  }
        stage('Pre-change validation') {
            steps {
              script {
                if (env.BRANCH_NAME == 'master') {
                  echo 'I only execute on the master branch'
                  sh "echo 'Placeholder for Pre-change validation'"
                  echo "currentBuild.currentResult: ${currentBuild.currentResult}"
                } else {
                    echo 'I execute elsewhere'
                }
              }
            }
        }
        stage('Simulate change in Sandbox') {
            steps {
                sh "echo 'Placeholder for policy simulation on Forward Sandbox'"
                echo "currentBuild.currentResult: ${currentBuild.currentResult}"
            }
        }
        stage('Apply network change') {
//            when {
//                expression { ${currentBuild.currentResult} == 'SUCESS' }
//            }
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
          echo "(Post always) currentBuild.currentResult: ${currentBuild.currentResult}"
          echo "(Post always) currentBuild.Result: ${currentBuild.result}"
          slackSend(channel: 'demo-notifications', message: 'test message from jenkins', username: 'fabriziomaccioni', token: 'GnbPV5e2SVkTkyMiRXaCFEXK', teamDomain: 'fwd-net')
//          color: 'good',
      }
      success {
          echo "(Post success) Pipeline executed successfully!"
      }
      unstable {
          echo "(Post unstable) Pipeline is unstable :/"
      }
      failure {
          echo "(Post failure) Pipeline Failed!!!"
      }
      changed {
          echo "(Post failure) Something changed..."
      }
    }
}
