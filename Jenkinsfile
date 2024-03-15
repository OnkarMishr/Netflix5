pipeline {
    agent any
    parameters {
        choice(name: 'ENVIRONMENT', choices: ['QA', 'UAT'], description: 'Select environment')
    }
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Build') {
            steps {
                script {
                    if (params.ENVIRONMENT == 'QA') {
                        sh 'sshpass -p "dev" scp target/Netflix5.war grras@172.17.0.2:/home/grras/appfiles/apache-tomcat-9.0.85/webapps'
                    } else if (params.ENVIRONMENT == 'UAT') {
                        sh 'cp target/Netflix5.war /home/onkar/Documents/Devops_Softawre/apache-tomcat-9.0.85/webapps'
                    } else {
                        echo 'No Choice Selected'
                    }
                }
            }
        }
    }
}
