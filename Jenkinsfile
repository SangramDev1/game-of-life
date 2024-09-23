pipeline {
    agent { label 'python' }
    
    stages {
        stage("Source Code") {
            steps {
                git branch: 'sprint1_develop', url: 'https://github.com/SangramDev1/game-of-life.git'
            }
        }

        stage("Build the Code") {
            steps {
                sh '''
                    export M2_HOME='/opt/apache-maven-3.9.8'
                    export PATH="$M2_HOME/bin:$PATH"
                    mvn package
                '''    
            }
        }

        stage("Archiving the Artifacts and Test Results") {
            steps {
                junit '**/surefire-reports/*.xml'
                archiveArtifacts artifacts: '**/*.war', followSymlinks: false
            }
        }
    }
}
