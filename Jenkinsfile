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

    options {
        timestamps()
    }

    stages {
        stage('Code Checkout') {
            steps {
                script {
                    checkout([$class                          : 'GitSCM',
                            branches                          : [[name: '*/master']],
                            doGenerateSubmoduleConfigurations : false,
                            extensions                        : [[$class: 'RelativeTargetDirectory',
                                                                  relativeTargetDir: 'pygit']],
                            submoduleCfg                      : [],
                            userRemoteConfigs                 : [[credentialsId: 'lee',
                                                                  url: 'git@github.com:lee-ch/pygit-utils.git']]])
                }
            }
        }
        stage('Check Environment') {
            steps {
                dir('pygit') {
                    sh 'pwd'
                    echo "${env.DOCKER_LABEL}"
                }
            }
        }
    }
}