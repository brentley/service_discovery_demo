# Service Discovery Demo

# build services from ecsworkshop.com

# build c9 environment INSIDE the same VPC as the ecsworkshop services

# in small top terminal pay attention to existing DNS results
watch -n1 -d 'host ecsdemo-nodejs.service | sort -n'

# see running tasks
ecs-cli compose --project-name ecsdemo-nodejs service ps \
    --cluster-config fargate-demo --desired-status RUNNING

# kill task in zone A (replace task id with id from above)
aws ecs stop-task --cluster $clustername \
    --task 2480bdf6-9b12-4d92-a2fc-58d6b381c26a
    
# see running and stopped tasks
ecs-cli compose --project-name ecsdemo-nodejs service ps \
    --cluster-config fargate-demo 
