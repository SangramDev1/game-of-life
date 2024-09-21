// Scripted Pipeline
node('python') {

    stage('checkout source code') {
        git branch: 'sprint1_develop', url: 'https://github.com/SangramDev1/game-of-life.git'
    }

    stage('build') {
        sh '''
            export M2_HOME='/opt/apache-maven-3.9.8'
            export PATH="$M2_HOME/bin:$PATH"
            mvn package
        '''
    }

    stage('archive artifact and test results') {
        junit '**/surefire-reports/*.xml'
        archiveArtifacts artifacts: '**/*.war', followSymlinks: false
    }
}
