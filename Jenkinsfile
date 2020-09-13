// Declarative //
def artifactVersion
pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
// Script //
node {
    stage('Build') {
        echo 'Building....'
        artifactVersion=getVersion()
        echo + ${artifactVersion}
    }
    stage('Test') {
        echo 'Building....'
    }
    stage('Deploy') {
        echo 'Deploying....'
    }
}

def getVersion() {
      readFile(env.WORKSPACE+"/build.gradle").split("\n").each { line ->
          if ((line =~ /version (.*)/).count > 0) {
            echo line
            def m = (line =~ /version (.*)/)[0]
            echo m[1].replaceAll('"','').trim()
            return m[1].replaceAll('"','')
          }
      }
}
