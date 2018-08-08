#!groovy

stage 'Dev'
node ('linux') {
    checkout scm
    mvn 'mvn clean package'
    dir('target') {stash name: 'war', includes: 'x.war'}
}

stage 'QA'
parallel(longerTests: {
    runTests(30)
}, quickerTests: {
    runTests(20)
})

stage name: 'Staging', concurrency: 1
node ('linux') {
    deploy 'staging'
}

input message: "Does staging look good?"
try {
    checkpoint('Before production')
} catch (NoSuchMethodError _) {
    echo 'Checkpoint feature available in CloudBees Jenkins Enterprise.'
}

stage name: 'Production', concurrency: 1
node ('linux'){
    echo 'Production server looks to be alive'
    deploy 'production'
    echo "Deployed to production"
}

def mvn(args) {
    sh "${args}"
}

def runTests(duration) {
    node {
        sh "sleep ${duration}"
        }
    }

def deploy(id) {
    unstash 'war'
    sh "cp x.war /tmp/${id}.war"
}

def undeploy(id) {
    sh "rm /tmp/${id}.war"
}
