node('python') {

    stage('checkout source code') {
        git branch: 'sprint1_develop', url: 'https://github.com/SangramDev1/game-of-life.git'
    }

    stage('build') {
        sh 'mvn package'
    }

    stage('archive artifact and test results') {
        junit '**/surefire-reports/*.xml'
        archiveArtifacts artifacts: '**/*.war', followSymlinks: false
    }
}
