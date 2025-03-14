node {
    checkout scm
    // Build
    stage("Build") {
        docker.image('composer:2').inside('-u root') {
            sh 'rm composer.lock'
            sh 'composer install'
        }
    }
    // Testing
    stage("Test") {
        docker.image('ubuntu').inside('-u root') {
            sh 'echo "Ini adalah test"'
        }
    }
    // Deploy (simulasi ke direktori lain, bisa diganti atau dihapus)
    stage("Deploy") {
        sh 'mkdir -p /var/jenkins_home/laravel-deploy'
        sh 'cp -r ./ /var/jenkins_home/laravel-deploy/'
        sh 'rm -rf /var/jenkins_home/laravel-deploy/.git'
    }
}
