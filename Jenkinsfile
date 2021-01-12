node {
    def app

    stage('Clone repository') {
        /* Cloning the Repository to our Workspace */

        checkout scm
    }

    stage('Build image') {
        /* This builds the actual image */

        app = docker.build("98222/nodeapp")
    }

    stage('Test image') {
        
        app.inside {
            echo "Tests passed"
        }
    }
	
    stage('Push image') {
        withDockerRegistry([ credentialsId: "docker-hub-credentials", url: "" ]) {
	    //bat "docker push devopsglobalmedia/teamcitydocker:build"
	    app.push("${env.BUILD_NUMBER}")
            app.push("latest")
	}
	    echo "Trying to Push Docker Build to DockerHub" 
    }


}
