node{
    stage('Git Checkout'){
      git 'https://github.com/ikramshahbaz/DevopsBootCamp-war-01.git'
    }
    stage('mvn clean'){
        sh 'mvn clean'
    }
    stage('mvn build'){
         sh 'mvn package'
    }
        stage('Build docker image'){
        sh 'docker build -t ikramshahbaz/devops-image-war:1.0 .'
    }
        stage('Docker Push image'){
        withCredentials([string(credentialsId: 'secrets', variable: 'secret1')]) { 
        sh 'docker login -u ikramshahbaz -p "${secret1}"'  
	}
        sh 'docker push ikramshahbaz/devops-image-war:1.0'
    }
        stage("Pull Container"){
        sh 'docker pull ikramshahbaz/devops-image-war:1.0'
    }
        stage("Run Container"){
        sh 'docker run -idt -p 8887:8887 ikramshahbaz/devops-image-war:1.0'
    }
}
