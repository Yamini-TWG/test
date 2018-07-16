#!/usr/bin/env groovy

properties(
        [parameters([
                booleanParam(defaultValue: false, description: 'build branch', name: 'branch_name')
				])]
static def get_branch_type(String branch_name) {
    //Must be specified according to <flowInitContext> configuration of jgitflow-maven-plugin in pom.xml
    def dev_pattern = ".*develop"
    def release_pattern = ".*release/.*"
    def feature_pattern = ".*feature/.*"
    def hotfix_pattern = ".*hotfix/.*"
    def master_pattern = ".*master"
    if (branch_name =~ dev_pattern) {
        return "dev"
    } else if (branch_name =~ release_pattern) {
        return "release"
    } else if (branch_name =~ master_pattern) {
        return "master"
    } else if (branch_name =~ feature_pattern) {
        return "feature"
    } else if (branch_name =~ hotfix_pattern) {
        return "hotfix"
    } else {
        return null
    }
}



//parallel(
//   "stream 1" : {
 //                  node {
 //                         echo 'Hello World'
//                        }
//                },
//   "stream 2" : { 
 //                    node { 
  //                         echo 'Hello World2'                                                       
  //                        } 
  //                 }
   //       )
