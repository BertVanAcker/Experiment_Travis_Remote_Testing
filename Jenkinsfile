pipeline {
  agent any
  environment {
        PIO_USERNAME     = credentials('PIO_USERNAME')
        PIO_PASSWORD     = credentials('PIO_PASSWORD')
    }
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
  stage('LOGOUT') {
        steps {
            sh 'pio account logout || true '
        }
	}	
  stage('LOGIN') {
        steps {
            sh 'pio account login --username $PIO_USERNAME --password "PIO_PASSWORD" '
        }
	}	
  stage('Compile and link + Flash on the buildserver (remote)') {
        steps {
            sh 'pio remote -a buildserver run --force-remote -t upload -e uno --upload-port COM3'
        }
	}
  }
}

