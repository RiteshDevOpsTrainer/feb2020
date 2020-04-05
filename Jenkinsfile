node {
	
	stage('Preparation'){
	  git 'https://github.com/RiteshDevOpsTrainer/feb2020.git'
	}
	
	stage('Build'){
	  def mvnHome = tool 'M2_HOME'
	  withEnv(["MVN_HOME=$mvnHome"]){
	    sh '"$MVN_HOME/bin/mvn" clean install compile package'
	  }
	}
	
	stage('Deploy'){
	  deploy adapters: [tomcat9(credentialsId: 'c3f4ac7f-60a7-422e-be38-f20fbd80c465', path: '', url: 'http://192.168.1.104:9080')], contextPath: null, onFailure: false, war: '**/*.war'
	}
	
	stage('Notification'){
	 emailext attachLog: true, body: '''Hi User, please find your project status''', subject: 'Jenkins Pipeline Build ', to: 'ritesh.goyal590@gmail.com'
	}
	
	stage('Print'){
	 sh 'echo "The DevOps Pipeline project is successfull"'
	}
}   
