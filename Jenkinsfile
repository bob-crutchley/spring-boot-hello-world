node {
	stage("maven package") {
		sh "ls -al"
		sh "mvn clean package"
	}
	stage("install new jar") {
		sh "ls -al target"
	}
	stage("restart service") {

	}
}
