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
                    withMaven(maven: 'maven') {
                        sh 'mvn clean install'
		
		}                        
		}
		    }

		stage('deploy') {
                    steps{
		    sh 'sshpass -p ubuntu scp /home/ubuntu/.jenkins/workspace/aws_build/target/data_trainings.war ubuntu@18.188.183.10:/home/ubuntu/soft/apache-tomcat-8.0.53/webapps'
		  
		    }
		    }
	    
		stage('start tomcat') {
                    steps{
		    sh 'sshpass -p ubuntu  ubuntu@18.188.183.10:/home/ubuntu/soft/apache-tomcat-8.0.53/bin/startup.sh'
		  
		    }
		    }
	    
    }
}
