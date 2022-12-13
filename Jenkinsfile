pipeline {
  agent any
stages{
  stage('Install Platformio') {
        steps {
            sh 'python -m pip install -U platformio'
        }
	}
  stage('Update Platformio') {
        steps {
            sh 'pio pkg update'
        }
	}
  stage('Compile and link + Flash on the buildserver (remote)') {
        steps {
            sh 'pio remote -a buildserver run --force-remote -t upload -e uno --upload-port COM3'
        }
	}
  }
}

