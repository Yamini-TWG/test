



   node {
   parallel (
     phase1: { sh "echo p11" },
     phase2: { sh "echo p2; sleep 40s; echo phase2" }
   )
  sh "run this after both phases complete"   
}
