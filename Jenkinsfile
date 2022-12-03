pipeline {
    agent any
    environment {
        // declarign custom env vars
        NEW_VERSION = '1.3.0'
        SERVER_CREDENTIALS = credentials('server-credentials') // credentials binding plugin
    }
    stages {
        stage("run frontend"){
            steps {
                echo 'starting react app'
                echo "building version ${NEW_VERSION}" // must use "" to interpret ${} correctly
                nodejs('Node-18'){
                    // cd into my-app directory
                    dir("my-app"){
                        sh 'npm install'
                    }
                    
                }
            }
        }
        stage("test"){
            when {
                expression {
                    BRANCH_NAME == 'dev'
                }
            }
            steps{
                echo 'when triggered'
            }
        }
        stage("deploy"){
            steps{
                withCredentials([
                    usernamePassword(credentialsId: 'server-credentials', usernameVariable: 'USER', passwordVariable: 'PWD')
                ]) {
                    echo "${USER} AND ${PWD}"
                }
            }
        }
    }
    // executed after all stages executed
    post {
        always {
            echo 'always runs'
        }
        success{
            echo 'success'

        }
        failure{
            echo 'failed'
        }

    }
}