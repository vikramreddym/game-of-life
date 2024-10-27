node('JDK8') {
    env.JAVA_HOME = '/usr/lib/jvm/java-8-openjdk-amd64'
    env.PATH="${env.JAVA_HOME}/bin:${env.PATH}"
    stage('SourceCode') {
        git branch: 'sprint1 develop', url: 'https://github.com/wakaleo/game-of-life.git'
    }
    stage('Build the code'){
        
        sh 'mvn clean package'
    }
    stage('Archiving artifacts & Junit test results') {
        junit stdioRetention: '', testResults: 'target/surefire-reports/*.xml'
        archiveArtifacts artifacts: '**/*.war', followSymlinks: false
    }
}