pipeline {
    agent any
    stages {
        stage("run frontend"){
            steps {
                echo 'starting react app'
                nodejs('Node-18'){
                    sh 'npm install'
                }
            }
        }
    }
}