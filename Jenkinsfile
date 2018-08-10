def label = "worker-${UUID.randomUUID().toString()}"

podTemplate(label: label, containers: [
  containerTemplate(name: 'maven', image: 'maven:3-jdk-8-alpine', command: 'cat', ttyEnabled: true),
]) {
  node(label) {
    stage("Git Checkout"){
	checkout scm
    }
    stage("Maven Build"){
	container('maven') {
	    sh "mvn clean install"
	}
    }
  }
}
