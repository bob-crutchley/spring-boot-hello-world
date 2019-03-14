node {
	stage("clone repository") {
		git "https://github.com/bob-crutchley/spring-boot-hello-world"
	}
	stage("maven package") {
		sh "mvn clean package"
	}
	stage("install new jar") {
		sh "sudo cp target/hello-world-0.0.1-SNAPSHOT.jar /home/spring/app.jar"
		sh "sudo chown spring:spring /home/spring/app.jar"
	}
	stage("restart service") {
		sh "sudo systemctl restart spring"	
	}
}
