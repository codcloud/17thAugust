#!/usr/bin/env/ groovy

import hudson.model.*
import hudson.EnvVars
import java.net.URL
node{
    stage('Git Checkout'){
        git 'https://github.com/codcloud/DevOpsClassCodes.git'
    }
    stage('compile'){
        withMaven(maven:'mymaven'){
            sh 'mvn compile'
        }
    }
    stage('Review'){
        withMaven(maven:'mymaven'){
            sh 'mvn pmd:pmd'
        }
        stage('Test'){
        withMaven(maven:'mymaven'){
            sh 'mvn test'
        }
            stage('Coverage'){
        withMaven(maven:'mymaven'){
            sh 'mvn cobertura:cobertura -Dcobertura.report.format=xml'
        }
    stage('Package'){
        withMaven(maven:'mymaven'){
            sh 'mvn package'
        }
    }
}
