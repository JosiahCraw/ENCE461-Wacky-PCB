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
        sh 'find *.SchDoc | xargs -I \'{}\' bash -c \'python /renderer/python-altium/altium.py {}.SchDoc > {}.svg\''
      }
    }

  }
}