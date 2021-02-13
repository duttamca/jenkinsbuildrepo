

 pipeline {
   agent any
   stages {
        stage('Checkout') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: 'master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'jenkins-user-github', url: 'https://github.com/duttamca/spring-gradle-mvc.git/']]])

            }
        }
        stage ('Build') {
        	steps {
        		sh './gradlew clean build'
        	}
         }
        stage ('Push to Remote ') {
            steps {
                sh 'echo workspace directory ${WORKSPACE}'
            }
         }
    }
}