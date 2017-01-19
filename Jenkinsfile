
node {
    stage('Pulling the repo') {
        git url: "https://github.com/zdebra/jenkinspipeline.git"
    }
    stage('Installing dependencies') {
        sh "npm i"
    }
    stage('Test') {
        sh "npm test"
    }
    stage('Deploy') {
        sh script: "./deploy.sh"
    }
}