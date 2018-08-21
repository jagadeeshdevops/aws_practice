pipeline{
          agent any
    stages{
        stage('printing hostname') {
            steps{
                sh 'hostname'
                sh 'hostname -i'
	}
	   }
                stage('build') {
                steps{
                    withMaven(maven: 'M2_HOME') {
                        sh 'mvn clean install'
		
		}                        
		}
		    }

		stage('deploy') {
                    steps{
		    withMaven(maven: 'M2_HOME') {
                                    sh 'sshpass -p ubuntu scp /home/ubuntu/.jenkins/workspace/aws_build/target/data_trainings.war ubuntu@18.191.185.169:/home/ubuntu/soft/apache-tomcat-8.0.53/webapps'
		}             
		    }
		    }
    }
}
