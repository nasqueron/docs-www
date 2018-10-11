pipeline {
    agent {
        label "node"
    }

    stages {
        stage('Doc') {
            steps {
                git 'https://devcentral.nasqueron.org/source/docs-www.git'

                sh '''
                npm install
                npm run build
                cd dist
                tar czf ../www-nasqueron-docs.tar.gz *
                '''
            }
            post {
                success {
                    archiveArtifacts artifacts: 'www-nasqueron-docs.tar.gz'
                }
            }
        }

        stage('Publish') {
            steps {
                sshPublisher(
                    failOnError: true,
                    publishers: [
                        sshPublisherDesc(
                            configName: 'ysul-deploy',
                            transfers: [
                                sshTransfer(
                                    sourceFiles: 'www-nasqueron-docs.tar.gz',
                                    remoteDirectory: 'workspace',
                                    cleanRemote: true,
                                    execCommand: 'tar xzvf workspace/www-nasqueron-docs.tar.gz -C /var/wwwroot/nasqueron.org/docs/'
                                )
                            ]
                        )
                    ]
                )
            }
        }
    }
}
