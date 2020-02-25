pipeline {
  agent any
  stages {
    stage('Render') {
      agent {
        dockerfile {
          filename 'ci/render/Dockerfile'
        }

      }
      steps {
        sh 'find *.SchDoc | xargs -I \'{}\' bash -c \'cd /renderer/python-altium && python altium.py {} > {}.svg\''
      }
    }

  }
}