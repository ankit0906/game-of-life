pipeline {
    agent { node { label 'built-in'
    customWorkspace '/home/ec2-user' }
    }
   
     stages {
        stage('checkout') {
            steps {
	        sh '''
	         rm -rf *
                git clone https://github.com/ankit0906/game-of-life.git
	         '''		
            }
        }
	 stage('build') {
            steps {
		 sh '''
                    sudo su
                    cd /home/ec2-user/game-of-life/
	            mvn clean install
                    '''
            }
        }
          stage('Deploy') {
            steps {
            sh ' cp game-of-life/gameoflife-web/target/gameoflife.war  /mnt/apache-tomcat-9.0.81/webapps ' 
			
            }
        }		

    }
}
