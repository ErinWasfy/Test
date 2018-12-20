node {
    stage ("checkout") {
         git(
       url: 'https://github.com/TestUserEME/Test.git',
       credentialsId: 'githubaccount',
       branch: "master"
    )
    }
    stage("test") {
        sh('bin/run_all_tests.sh')
    }
    def tag = sh(returnStdout: true, script: "git tag --contains | head -1").trim()
    if (tag) {
        stage("deploy") {
            sh('bin/build_and_publish.sh')
        }
    }
}
