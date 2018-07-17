node {
   echo 'Hello World, I am branch test'
 //  echo "${env.'GIT_BRANCH'}"
   //echo "${GIT_BRANCH}"
   checkout([$class: 'GitSCM', branches: [[name: '$GIT_BRANCH']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: '62ae77a3-44c9-412f-9e70-f6682bff945e', url: 'https://github.com/Yamini-TWG/test.git']]]
   
   
}
