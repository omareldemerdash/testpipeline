pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        sh '''echo ">>>>>>>>> Start Clearing old docker images"
if docker images -a | grep "omareldemerdash28/nodejs-react*" | awk \'{print $1":"$2}\' | xargs docker rmi -f; then
    printf \'Clearing old images succeeded\\n\'
else
    printf \'Clearing old images failed\\n\'
fi'''
        sh '''docker build -t omareldemerdash28/nodejs-react:$BUILD_NUMBER .
docker login -u $USERNAME -p $PASSWORD
docker push omareldemerdash28/nodejs-react:$BUILD_NUMBER'''
      }
    }

  }
}