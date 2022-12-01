pipeline {
    agent any

    environment {
        BRANCH = "master"
    }

    triggers {
        cron('0 8 * * 1')
    }

    options {
        skipDefaultCheckout true
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Dtrack') {
            steps {
                script {
//                    sh 'pip install cyclonedx-bom'
//                    sh 'cyclonedx-bom --requirements -i app/requirements.txt'
//                   dependencyTrackPublisher(
//                        artifact: 'cyclonedx.xml',
//                        projectName: 'minimal-project-python',
//                        projectVersion: 'app',
 //                   )
                    sh "npm install"
                    sh "npx @cyclonedx/bom@3.10.6 --include-dev -o bom.xml"
                    dependencyTrackPublisher(
                        artifact: "bom.xml",
                        projectName: "minimal-project-npm",
                        projectVersion: "npm"
                    )                    
                }
            }
        }
    }
}