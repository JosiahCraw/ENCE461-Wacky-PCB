pipeline {
  agent none
  stages {
    stage('Render') {
      agent {
        dockerfile {
          filename 'ci/render/Dockerfile'
        }

      }
      steps {
        sh 'cp -r /renderer/python-altium/* .'
        sh 'find *.SchDoc | xargs -I \'{}\' bash -c \'python altium.py {} > {}.svg\''
      }
    }

  }
}