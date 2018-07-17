
//env.PATH = '/usr/local/bin:/usr/bin:/bin:/usr/sbin:/sbin:'
//env.LC_ALL='en_US.UTF-8'
//env.LANG='en_US.UTF-8'

pipeline {
	agent any
	stages {
		stage('Checkout code') {
			checkout scm
		}

		stage ('unit test') {
			echo "I am unit test"
			//sh 'bundle exec fastlane unit_tests'
		}
	}
}
post {
  success {
    input {
      message 'choose parameters'	
 	  ok 'deploy'
	  parameters {
		choice(choices: 'app-store\nad-hoc\ndevelopment', description:'determines which type of provisioning profile is used.', name: 'buildExportMethod')
		choice(choices: 'development\ncontent\nstaging\nuat\nrelease', description: 'determines which app flavor/ build configuration is used.', name: 'environment')
		string(defaultValue: '0.9.9', description: 'sets the version number of the app', name: 'versionNumber')
		string(defaultValue: '1', description: 'sets the build number of the app', name: 'buildNumber')
              }
		 }
  }
	stages {
		stage ('Checkout code') {
			checkout scm
		}

		stage ('adjust app version') {
			echo "version:${params.version}"
			//sh 'bundle exec fastlane adjust_version_and_build_number version:${params.version} build_number:${params.build_number}'
		}

		stage ('build ipa') {
			echo "build_export_method:${params.buildExportMethod}"
			//sh 'bundle exec fastlane build build_export_method:${params.buildExportMethod} --env ${params.environment}'
		}

		stage ('upload to crashlytics') {
			echo "crash"
			//sh 'bundle exec fastlane upload_crashlytics --env ${params.environment}'
		}

	}
failure {
         echo 'unit test fail'
	}
}

