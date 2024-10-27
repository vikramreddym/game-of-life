node('JDK8') {
    env.JAVA_HOME = "${tool 'JDK8'}"
    env.PATH="${env.JAVA_HOME}/bin:${env.PATH}"

    def mvnHome = tool name: '3.8.4', type: 'maven'
    env.PATH = "${mvnHome}/bin:${env.PATH}"

    stage('SourceCode') {
        git branch: 'scripted-declarative', url: 'https://github.com/vikramreddym/game-of-life.git'
    }
    stage('Build the code'){
        
        sh 'mvn clean package'
    }
    stage('Archiving artifacts & Junit test results') {
        junit stdioRetention: '', testResults: 'gameoflife-web/target/surefire-reports/*.xml'
        archiveArtifacts artifacts: '**/*.war', followSymlinks: false
    }
}