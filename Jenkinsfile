#!groovy

node {

  stage "Checkout Git repo"
    checkout scm
  stage "Build RPM"
    sh "[ -d ./rpm ] || mkdir ./rpm"
  stage "Update YUM repo"
    sh "[ -d ~/repo/rpm/demo-app/ ] || mkdir -p ~/repo/rpm/demo-app/"
    sh "mv ./rpm/*.rpm ~/repo/rpm/demo-app/"
    sh "createrepo ~/repo/"
  stage "Check YUM repo"
    sh "yum clean all"
    sh "yum info demo-app-\$(git rev-parse --short HEAD)"
}
