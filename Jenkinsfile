def doRelease = 1

node {
    stage('Promote?') {
        sh 'git describe --tags > describe.txt'
        currentBuild.description = readFile 'describe.txt'
        try {
            input 'Release'
        }
        catch (exc) {
            echo 'Something failed, I should sound the klaxons!'+exc
            currentBuild.result = 'SUCCESS'
            doRelease = 0
        }
    }
    stage('Promote!') {
      if (doRelease > 0) {
        echo 'Released >> describe.txt'
        currentBuild.description = readFile 'describe.txt'
      } else {
        echo "not"
      }
    }
}
