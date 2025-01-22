pipeline{
     agent {
        label 'AGENT-1'
    }
    options{
        timeout(time: 30, unit: 'MINUTES')
        disableConcurrentBuilds()
        //retry(1)
    }
     environment {
        appVersion = '' // this will become global, we can use across pipeline
        region = 'us-east-1'
        account_id = '315069654700'
        project = 'expense'
        environment = 'dev'
        component = 'backend'
    }

    stages{
        stage('read the version'){
            steps{
                script{
                    def packageJson = readJSON file: 'package.json'
                    appVersion = packageJson.version
                }
            }
        }
         stage('install dependencies'){
            steps{
                sh 'npm install'
            }
        }
    }
}