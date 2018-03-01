def doRelease = 1

node {
    stage('Promote?') {
        currentBuild.description = $(git describe --tags)
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
        currentBuild.description = "$(git describe --tags) \nReleased"
      } else {
        echo "not"
      }
    }
}
