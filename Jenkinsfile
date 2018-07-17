



    node {
            stage ('Checkout code from Git')
            // Checkout code from repository
            checkout scm

            echo "============================="
            echo " Build Options:"
            echo "Qat: ${params.Qat}"
            echo "Staging: ${params.Staging}"
            echo "Prod: ${params.Prod}"
            echo "Content: ${params.Content}"
            echo "Crashlytics Upload: ${params.Crashlytics}"
            echo "Playstore Upload: ${params.Playstore}"
            echo "============================="

           env branch_type == "release"
	    if(branch_type == "release"){
                //Build all the variants and upload in Crashlytics
                //This is release branch
                println 'This happens only on release branch'
            }else if (branch_type == "feature"){
                println 'This happens only on feature branch'
            }
parallel (
            if(params.Prod || params.Playstore){
                stage 'Build Prod'
                println "Building Prod flavor"
               //h "./gradlew assembleProdRelease"

                if(params.Crashlytics){
                    stage 'Upload Prod to Beta (Crashlytics)'
                  println "Uploading Prod to Beta (Crashlytics)"
                 // sh "./gradlew crashlyticsUploadDistributionProdRelease"
                }
            }


            if(params.Staging){
                stage 'Build Staging'
                println "Building Staging flavor"
                sh "./gradlew assembleStagingRelease"

                if(params.Crashlytics){
                    stage 'Upload Staging to Beta (Crashlytics)'
                    println "Uploading Staging to Beta (Crashlytics)"
                    sh "./gradlew crashlyticsUploadDistributionStagingRelease"
                }
            }

            if(params.Qat){
                stage 'Build Qat'
                println "Building Qat flavor"
            //  sh "./gradlew assembleQatRelease"

                if(params.Crashlytics){
                    stage 'Upload Qat to Beta (Crashlytics)'
                    println "Uploading Qat to Beta (Crashlytics)"
                  // h "./gradlew crashlyticsUploadDistributionQatRelease"
                }
            }

            if(params.Content){
                stage 'Build Content'
                println "Building Content flavor"
              //sh "./gradlew assembleContentRelease"

                if(params.Crashlytics){
                    stage 'Upload Content to Beta (Crashlytics)'
                    println "Uploading Content to Beta (Crashlytics)"
                 // sh "./gradlew crashlyticsUploadDistributionContentRelease"
                }
           }
		   )
           

