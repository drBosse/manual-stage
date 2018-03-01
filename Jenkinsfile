node {
    stage('Example') {
        try {
            Input 'Release'
        }
        catch (exc) {
            echo 'Something failed, I should sound the klaxons!'+exc
            currentBuild.result = 'SUCCESS'
        }
    }
}
