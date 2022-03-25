pipeline {
     agent any
     
    stages {
        stage('clone-repo') {
            steps {
                git 'https://github.com/nageshvkn/gamutkart2.git'
            }
        }
        stage('build') {
            steps {
                sh 'mvn install -Dmaven.test.skip=true'
            }
        }
         stage('test-case') {
            steps {
                sh 'mvn install'
            }
        }  
         stage('deployment') {
            steps {
                sh 'sshpass -p "ram" scp target/flipkart.war ram@172.17.0.4:/home/ram/apache-tomcat-9.0.60/webapps'
                sh 'sshpass -p "ram" ssh ram@172.17.0.4 /home/ram/apache-tomcat-9.0.60/bin/startup.sh'
            }
        }
    }
}
