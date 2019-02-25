pipeline {
    agent { 
		docker{
			image 'alirizasaral/maven-with-proxy:latest'
			label 'vm'
			args  '-e PROXY_HOST=web-proxy.corp.hpecorp.net -e PROXY_PORT=8080'
		}
	}
    stages {
       // stage ('Checkout') {
       //   steps {
       //     git 'https://github.com/effectivejenkins/spring-petclinic.git'
       //   }
       // }
        stage('Build') {
            //agent { docker 'maven:3.5-alpine' }
            steps {
                sh 'mvn clean package'
                junit '**/target/surefire-reports/TEST-*.xml'
               // archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
            }
        }
        //stage('Deploy') {
        //  steps {
        //    input 'Do you approve the deployment?'
        //    sh 'scp target/*.jar jenkins@192.168.50.10:/opt/pet/'
        //    sh "ssh jenkins@192.168.50.10 'nohup java -jar /opt/pet/spring-petclinic-1.5.1.jar &'"
        //  }
        // }
    }
}
