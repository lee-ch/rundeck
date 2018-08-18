#!groovy
pipeline {
    environment {
        DOCKER_LABEL = 'rundeck'
    }

    agent {
        label {
            label 'docker'
        }
    }
    stages {
        stage('Code Checkout') {
            steps {
                script {
                    checkout([$class:                               'GitSCM',
                            branches:                             [[name: '*/master']],
                            doGenerateSubmoduleConfigurations:    false,
                            extensions:                           [[$class:           'RelativeTargetDirectory',
                                                                    relativeTargetDir: 'pygit-utils']],
                            submoduleCfg:                         [],
                            userRemoteConfigs:                    [[credentialsId: 'lee', url: 'git@github.com:lee-ch/pygit-utils.git']]])
                }
            }
        }
    }
}