node {
    checkout scm
    // Build
    stage("Build") {
        docker.image('shippingdocker/php-composer:8.3').inside('-u root') {
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
        sh 'mkdir -p /home/hafidwahyudi/laravel-deploy'
        sh 'cp -r ./ /home/hafidwahyudi/laravel-deploy/'
        sh 'rm -rf /home/hafidwahyudi/laravel-deploy/.git'
    }
}
