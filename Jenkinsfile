pipeline {
  agent {
    node {
      label 'ubuntu'
    }

  }
  
  stages {
    stage('Checkout') {
      steps {
        sh 'echo $sha1'
        // Get nuttx from GitHub
        checkout([  
            $class: 'GitSCM', 
            doGenerateSubmoduleConfigurations: false, 
            extensions: [[$class: 'RelativeTargetDirectory', relativeTargetDir: 'nuttx']], 
            submoduleCfg: [], 
            userRemoteConfigs: [[credentialsId: 'd7d5d54b-d4f7-4422-ad58-6b5fde78ee52', url: 'https://github.com/maht/incubator-nuttx.git', refspec: '+refs/pull/${ghprbPullId}/*:refs/remotes/origin/pr/${ghprbPullId}/*']]
        ])
      }
    }

    stage('Admit') {
      steps {
        sh 'echo "Admitted!"'
      }
    }

    stage('Build') {
      steps {
        sh 'echo "Built!"'
      }
    }

    stage('Test') {
      steps {
        sh 'echo "Some minor test ..."'
        sh 'echo "Tested!"'
      }
    }

  }
  environment {
    EXAMPLE_ENV = 'example_value'
  }
}
