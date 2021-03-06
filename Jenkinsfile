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
        sh 'find *.SchDoc | xargs -I \'{}\' bash -c \'python altium.py {} > {}.svg\' || true '
        archiveArtifacts '*.svg'
        stash(includes: '*.svg', name: 'svg')
      }
    }

    stage('Build') {
      agent {
        dockerfile {
          filename 'ci/build/Dockerfile'
        }

      }
      steps {
        unstash 'svg'
        sh 'rsvg-convert -f pdf -o schematic.pdf *.svg'
        archiveArtifacts '*.pdf'
      }
    }

    stage('Upload') {
      agent any
      steps {
        withAWS(endpointUrl: 's3.sys-io.net', credentials: 'a45d1539-3eed-43ed-a23e-e30fc9b3913e') {
          s3Upload(bucket: 'jenkins-artifacts', path: 'Wacky-PCB/', includePathPattern: '**/*.svg')
        }

      }
    }

  }
}