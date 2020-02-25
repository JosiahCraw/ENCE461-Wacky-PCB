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
        sh 'cp *.SchDoc /renderer/python-altium/'
        sh 'cd /renderer/python-altium && find *.SchDoc | xargs -I \'{}\' bash -c \'python altium.py {}.SchDoc > {}.svg\''
      }
    }

  }
}