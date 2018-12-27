node {
    def version
    stage('Preparation') {
        checkout scm
        version = "0.53"
        echo "Building version ${version}"
        sh 'docker pull node:8-alpine'
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