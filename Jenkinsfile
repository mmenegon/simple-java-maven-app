def label = "worker-${UUID.randomUUID().toString()}"

podTemplate(label: label, containers: [
  containerTemplate(name: 'maven', image: 'jenkinsxio/builder-maven', command: 'cat', ttyEnabled: true),
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
