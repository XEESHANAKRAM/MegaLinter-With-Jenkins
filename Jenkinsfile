pipeline {
    agent {
        docker {
            image 'oxsecurity/megalinter-cupcake:v7.8.0'
            args '-u root' // Specify additional Docker arguments if needed
        }
    }
    environment {
        DISABLE = "SPELL"
        DISABLE_ERRORS = true
    }
    stages {
        stage('MegaLinter') {
            steps {
                script {
                    sh '/entrypoint.sh'
                }
            }
            post {
                always {
                    archiveArtifacts(allowEmptyArchive: true, artifacts: 'mega-linter.log,,megalinter-reports/**/*', defaultExcludes: false, followSymlinks: false)
                }
            }
        }
    }
}
