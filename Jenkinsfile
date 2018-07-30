node {
    def version
    stage('Preparation') {
        checkout scm
        version = "0.45.1"
        echo "Building version ${version}"
        sh 'docker pull debian:jessie'
    }
    stage('Build') {
        echo "Building version ${version}"
        sh "docker build -t taimos/hugo:${version} ."
    }
    stage('Publish') {
        sh "docker tag taimos/hugo:${version} taimos/hugo:latest"
        sh "docker push taimos/hugo:${version}"
        sh "docker push taimos/hugo:latest"
    }
}