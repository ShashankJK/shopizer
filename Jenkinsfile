pipeline {
agent any
tools {
	maven 'MAVEN_HOME'
        jdk 'JAVA_HOME'
}
stages {
stage ('Build') {
	steps {
		echo "Building Project"
		bat '''
			mvn clean install
		'''
	}
}
stage('Test') {
        steps {
             bat '''
             	  	mvn -B verify
             '''
        }
}
stage('Deploy') {
	steps {
		echo "Deploy"
		deploy adapters: [tomcat9(credentialsId: '9d8d0153-9c71-45ff-a818-2b352151947b', path: '', url: 'http://localhost:8080')], contextPath: 'Shopizer', war: '**/*.war'
	    }
    }
}
}
