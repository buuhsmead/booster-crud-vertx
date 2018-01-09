// path of the template to use
        // def templatePath = 'https://raw.githubusercontent.com/openshift/nodejs-ex/master/openshift/templates/nodejs-mongodb.json'
        // name of the template that will be created
        // def templateName = 'nodejs-mongodb-example'
        openshift.withCluster() {
          openshift.withProject() {
            echo "Using project: ${openshift.project()}"
            pipeline {
              agent {
                node {
                  // spin up a node.js slave pod to run this build on
                  label 'maven'
                }
              }
              options {
                // set a timeout of 20 minutes for this pipeline
                timeout(time: 20, unit: 'MINUTES')
              }
              stages {
                stage('cleanup') {
                }
                stage('checkout') {
                }
                stage('build') {
                  steps {
                    sh "mvn clean fabric8:deploy -Popenshift"
                  }
                }
              }
            }
          }
        }
