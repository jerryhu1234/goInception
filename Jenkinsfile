env.PROJ_DIR='src/learningGo'
node {
    withEnv(["GOPATH=$WORKSPACE"]) {     
        stage('Init gopath') {
            sh 'mkdir -p $GOPATH/{bin,pkg,src}'  
        }
        stage('Get code') {
            checkout([                      
                $class: 'GitSCM', 
                branches: [[name: '*/master']], 
                doGenerateSubmoduleConfigurations: false, 
                extensions: [[$class: 'RelativeTargetDirectory', relativeTargetDir: 'src/learningGo']], 
                submoduleCfg: [], 
                userRemoteConfigs: [[
                    credentialsId: '3d33494a-ee1a-4540-a5e9-27f068a2b859', 
                    url: 'git@github.com:peng0208/learningGo.git'
                ]]
            ])
        }
        stage('Build go proejct') {      
            sh 'cd ${PROJ_DIR}/daemon/example; go test && go build && go install'
        }
        stage('Deploy to test') {          
            input message: 'deploy to test ?', ok: 'De'
            echo 'docker run'
        }
        stage('Deploy to qa') {             /
            input message: 'deploy to qa ?', ok: 'OK!'
            echo 'docker run'
        }
        stage('Deploy to production') {     
            input message: 'deploy to production ?', ok: 'OK!'
            echo 'docker run'
        }
    }
}

