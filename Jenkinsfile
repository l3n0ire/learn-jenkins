pipeline {
    agent any
    stages {
        stage("run frontend"){
            steps {
                echo 'starting react app'
                nodejs('Node-18'){
                    // cd into my-app directory
                    dir("my-app"){
                        sh 'npm install'
                    }
                    
                }
            }
        }
    }
}