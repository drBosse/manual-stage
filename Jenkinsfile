node {
    stage('Example') {
        try {
            input 'Release'
        }
        catch (exc) {
            echo 'Something failed, I should sound the klaxons!'+exc
            currentBuild.result = 'SUCCESS'
        }
    }
}
