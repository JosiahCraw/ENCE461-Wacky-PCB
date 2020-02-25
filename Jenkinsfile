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
        sh 'cd /renderer/python-altium && find *.SchDoc | xargs -I \'{}\' bash -c \'python altium.py {}.SchDoc > {}.svg\''
      }
    }

  }
}