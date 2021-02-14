

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
                sh 'mkdir -p ${WORKSPACE}/remotepush'
                sh 'cd ${WORKSPACE}/remotepush'
                sh 'cp ${WORKSPACE}/build/libs/workspace.war .'
                sh 'git init -b main'
                sh 'git add --all'
                sh 'git commit -m "first commit"'
                sh 'git remote add origin https://github.com/duttamca/jenkinsbuildrepo.git'
                sh 'git push origin main'
            }
         }
    }
}