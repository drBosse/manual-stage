def doRelease = 1

node {
    stage('Checkout') {
      checkout scm
      sh 'git fetch -pt'
    }
    stage('Build') {
      sh 'cat Jenkinsfile'
    }
    stage('Promote?') {
        sh 'git describe --tags > describe.txt'
        currentBuild.description = readFile 'describe.txt'
        sh 'date'
        try {
          timeout(time: 15, units: 'MINUTES') {
            input 'Release'
          }
        }
        catch (exc) {
            echo 'Something failed, I should sound the klaxons!'+exc
            currentBuild.result = 'UNSTABLE'
            doRelease = 0
        }
    }
    stage('Promote!') {
      if (doRelease > 0) {
        sh 'echo Released $(git describe --tags) > describe.txt'
        currentBuild.description = readFile 'describe.txt'
      } else {
        echo "not"
      }
    }
}
