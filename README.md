# [<img src="ecs-logo.png" width="30%">](https://aws.amazon.com/ecs/) [<img src="fargate-logo.png" width="33%">](https://aws.amazon.com/fargate/)

A curated list of guides, development tools, and resources for [Amazon Elastic Container Service](https://aws.amazon.com/ecs/) (ECS). This list includes both community created content as well as content created by AWS.

_Want to add something? Open a PR!_ 🙂

### Pick your container hosting strategy:

- <a href="#aws-fargate">AWS Fargate</a> - AWS Fargate is a technology for Amazon ECS that allows you to run containers without having to manage servers or clusters.
- <a href="#self-hosted-in-ec2">Self hosted in EC2</a> - Running your own cluster of EC2 instances to host your containers gives you the most control over price (ability to run on spot instances or reserved instances) as well as configuration.

<br />

## AWS Fargate

### Setting up Fargate

- [fargate](http://somanymachines.com/fargate/) - Command line tool for interacting with AWS Fargate. With just a single command you can build, push, and launch your container in Fargate, orchestrated by ECS.
- [CloudFormation Templates](https://github.com/nathanpeck/aws-cloudformation-fargate) - Sample CloudFormation templates to help you spin up a Fargate cluster, and service in that cluster automatically

### Application Deployments in Fargate

- [Deploying a Rails app to Fargate](http://blog.scoutapp.com/articles/2018/01/08/deploying-to-aws-part-i-running-a-rails-app-on-fargate) - Step by step walkthrough of deploying a Ruby + RDS app, with helpful debugging tips
- [How to use AWS Fargate and Lambda for long-running processes in a Serverless app](https://serverless.com/blog/serverless-application-for-long-running-process-fargate-lambda/) - Great tutorial showing how to leverage the power of long running docker containers in Fargate alongside Lambda. Example application processes video files to extract thumbnails using just S3, Lambda, and Fargate... no EC2.

<br />

## Self hosted in EC2

- <a href="#getting-started">Getting Started</a>
- <a href="#infrastructure-as-code">Infrastructure as Code</a>
- <a href="#build-and-deploy-tools">Build and Deploy Tools</a>
- <a href="#implementation-guides">Implementation Guides</a>
- <a href="#open-source">Open Source</a>
- <a href="#reference-architectures">Reference Architectures</a>
- <a href="#continuous-integration--continuous-deployment">Continuous Integration / Continuous Deployment</a>
- <a href="#presentations">Presentations</a>
- <a href="#tech-blogs">Tech Blogs</a>

### Getting Started
  - [The Hitchhikers Guide to AWS ECS and Docker](http://start.jcolemorrison.com/the-hitchhikers-guide-to-aws-ecs-and-docker/) by [J. Cole Morrison](https://twitter.com/JColeMorrison) - Introduction to AWS ECS concepts
  - [Working with AWS ECS](https://blog.rackspace.com/working-aws-ecs) by [Sriram Rajan](https://twitter.com/sriramrajan) of Rackspace

### Infrastructure as Code

Examples of using tools to describe your ECS infrastructure as code, for automation of deployments:

   - [mu](https://github.com/stelligent/mu) - Automates everything relating to ECS devops and CI/CD. This framework lets you write a simple metadata file and it constructs all the infrastructure you need so that you can deploy to ECS by simply pushing to your Git repo.
  - [CloudFormation ECS](https://github.com/awslabs/ecs-refarch-cloudformation) - Reference architecture for deploying microservices to ECS in tiered VPC with NAT gateways and two availability zones.
  - [Terraform ECS](https://github.com/arminc/terraform-ecs) by [Armin Coralic](https://twitter.com/acoralic) - Production ready AWS ECS infrastructure as code with Terraform
  - [CloudFormation Templates by Cloudonaut](https://cloudonaut.io/new-cloudformation-templates-ecs-cluster-service-legacy-vpc-wrapper-automated-tests/)
  - [ecsq](https://github.com/mightyguava/ecsq) - A developer friendly tool for querying the state of an ECS cluster
  - [deployfish](https://github.com/caltechads/deployfish) - Write a simplified `deployfish.yml` file describing your deployment and let this tool handle the heavy lifting of deploying your service.
  
### Build and Deploy Tools

Tools to help you interact with ECS to launch your containers on your cluster of self managed EC2 instances:

  - [coldbrew](https://github.com/coldbrewcloud/coldbrew-cli) - Fantastic tool that provisions ECS infrastructure, builds and deploys your container, and connects your services to an application load balancer automatically
  - [ecs-cli](https://github.com/aws/amazon-ecs-cli) - Docker Compose compatible deployment tool by AWS
  - [empire](https://github.com/remind101/empire/blob/master/README.md) - Control layer on top of ECS that provides a Heroku like workflow
  - [broadside](https://github.com/lumoslabs/broadside/) - Ruby based command line tool for deploying to ECS
  - [UFO](http://ufoships.com/) - Ruby based tool for building containers and shipping them to ECS
  - [bash deployment script](https://spin.atomicobject.com/2017/06/06/ecs-deployment-script/) by [Justin Kulesza](https://twitter.com/JustinKulesza)
  - [pnzr](https://github.com/jobtalk/pnzr) - Go based tool for building and pushing to ECS, also has integraton with AWS KMS for secrets management.
  - [deplojo](https://github.com/LabD/ecs-deplojo) - Python based deployment tool using ECS
  - [convox](https://convox.com/) - Easily build, deploy and scale applications on ECS
  - [ecsctl](https://github.com/cxmcc/ecsctl) - Open source tool similar to Kubernetes `kubectl` for ECS.
  - [ecs-deploy](https://github.com/silinternational/ecs-deploy) - Simple but powerful tool for initiating automatic blue green deploys on ECS
  - [ecspresso](https://github.com/kayac/ecspresso) - Minimalistic: JSON file goes in, service launches

### Implementation Guides

Examples of how to do advanced customizations on your ECS cluster:

  * <a name="autoscaling" /> __Autoscaling__
    - [Autoscaling services in ECS](https://www.codementor.io/jholub/amazon-ecs-auto-scale-docker-containers-6keydo24n) - How to autoscale the number of service tasks
    - [Autoscaling the cluster in ECS](http://garbe.io/blog/2016/10/17/docker-on-ecs-scale-your-ecs-cluster-automatically/) - How to autoscale the number of EC2 instances in a cluster
    - [Advanced ECS cluster autoscaling](http://garbe.io/blog/2017/04/12/a-better-solution-to-ecs-autoscaling/) - A more advanced technique for autoscaling an ECS cluster, with more effective scale in as well as out
    - [Lambda based approach for cluster scale-in](https://github.com/omerxx/ecscale)
    - [Extending ECS autoscaling for under $2 a month with Lambda](https://www.miketheman.net/2017/01/09/extending-ecs-auto-scaling-for-under-2month-with-lambda/)
    - [Scale in script in Python](https://medium.com/@dinushad92/scale-down-ec2-container-instances-in-ecs-fb97f895ac9c)
  * __Networking__
    - [Private subnets tutorial](https://www.topcoder.com/blog/aws-container-services-private-subnets-tutorial/)
  * <a name="service-discovery" /> __Service Discovery__
    - [Using DNS](https://github.com/awslabs/ecs-refarch-service-discovery/)
    - [Using Consul](https://aws.amazon.com/blogs/compute/service-discovery-via-consul-with-amazon-ecs/)
    - [Using Weaveworks](https://www.weave.works/blog/using-weave-to-network-containerized-microservices-on-amazon-ecs/)
    - [Using linkerd](https://medium.com/attest-engineering/linkerd-a-service-mesh-for-aws-ecs-937f201f847a)
  * __Data Persistance__
    - [Using Amazon Elastic File System](https://aws.amazon.com/blogs/compute/using-amazon-efs-to-persist-data-from-amazon-ecs-containers/)
  * __Secrets Management__
    - [Using Parameter Store and IAM Roles for Tasks](https://aws.amazon.com/blogs/compute/managing-secrets-for-amazon-ecs-applications-using-parameter-store-and-iam-roles-for-tasks/)
    - [Using ECS Task roles for managing AWS credentials](https://medium.com/@RemindEng/keeping-aws-secrets-secret-with-ecs-ec4a51517b4d)
    - [The right way to store secrets using Parameter Store](https://aws.amazon.com/blogs/mt/the-right-way-to-store-secrets-using-parameter-store/)
  * __Administration__
    - [Automatically draining cluster instances before termination](https://aws.amazon.com/blogs/compute/how-to-automate-container-instance-draining-in-amazon-ecs/)
    - [Monitor cluster state with Cloudwatch event stream](https://aws.amazon.com/blogs/compute/monitor-cluster-state-with-amazon-ecs-event-stream/)
    - [Run an ECS Task on every cluster instance](https://aws.amazon.com/blogs/compute/running-an-amazon-ecs-task-on-every-instance/)
  * __Docker for .NET Developers__
    - [Part One: Intro](https://www.stevejgordon.co.uk/docker-dotnet-developers-part-1)
    - [Part Two: Our First dockerfile](https://www.stevejgordon.co.uk/docker-for-dotnet-developers-part-2)

### Open Source
  - [Blox](https://blox.github.io/) - Framework for advanced cluster management and scheduling
  - [Watchbot](https://github.com/mapbox/ecs-watchbot) - This tool by [Mapbox](https://www.mapbox.com/) helps you run data processing across an ECS cluster in response to external events
  - [ecs-export](https://github.com/slok/ecs-exporter) - A tool for exporting ECS cluster metrics to Prometheus for advanced querying
  - [docker-elk-ecs](https://github.com/markriggins/docker-elk-ecs) - Connecting Amazon ECS container logs to an ELK (Elasticsearch, Logstash, Kibana) stack
  - [Sample task definitions](https://github.com/aws-samples/aws-containers-task-definitions) - Sample task definitions for running applications like Nginx, Tomcat, Gunicorn, Wildfly, Kibana, and Jetty as containers under Amazon ECS

### Reference Architectures
  - [Microservice cloudformation stack](https://github.com/awslabs/ecs-refarch-cloudformation)
  - [Sock shop microservices demo on Amazon ECS](https://microservices-demo.github.io/microservices-demo/deployment/ecs.html)
  - [Node.js Microservices](https://github.com/awslabs/amazon-ecs-nodejs-microservices)
  - [Java Microservices on AWS ECS](https://github.com/awslabs/amazon-ecs-java-microservices)
  - [Swift ECS Workshop](https://github.com/awslabs/swift-ecs-workshop)
  - [NGINX Reverse Proxy sidecar container on AWS ECS](https://github.com/awslabs/ecs-nginx-reverse-proxy)
  - [Deploying a Deep Learning Framework on ECS](https://github.com/awslabs/ecs-deep-learning-workshop)
  - [Powering your Amazon ECS Cluster with Amazon EC2 Spot Instances](https://github.com/awslabs/ec2-spot-labs/tree/master/ecs-ec2-spot-fleet)
  - [Reactive Microservices Architectures with Amazon ECS, AWS Lambda, Amazon Kinesis Streams, Amazon ElastiCache, and Amazon DynamoDB](https://github.com/aws-samples/reactive-refarch-cloudformation)

### Continuous Integration / Continuous Deployment
  * __CI/CD using:__
    - [AWS CodePipeline](https://github.com/awslabs/ecs-refarch-continuous-deployment)
    - [Atlassian Bamboo](https://bitbucket.org/atlassian/per-build-container)
    - [Lambda](https://medium.com/@YadavPrakshi/automate-zero-downtime-deployment-with-amazon-ecs-and-lambda-c4e49953273d)
    - [CircleCI](https://github.com/circleci/go-ecs-ecr)
    - [Shippable](http://blog.shippable.com/continuous-delivery-from-github-to-amazon-ecs)
    - [Gitlab](http://jeanphix.me/2017/06/14/how-to-configure-a-gitlab-ecs-continuous-deployment-pipeline/)
    - [SemaphoreCI](https://semaphoreci.com/community/tutorials/continuous-deployment-of-a-dockerized-node-js-application-to-aws-ecs)
  * __CI/CD mechanics:__
    - [Rolling blue/green deploy in place](https://blog.codeship.com/easy-blue-green-deployments-on-amazon-ec2-container-service/)
    - [Canary Deploy](https://github.com/awslabs/ecs-canary-blue-green-deployment)
    - [Isolated Regression Testing](https://aws.amazon.com/blogs/compute/amazon-ecs-at-the-climate-corporation-using-ecr-and-multiple-accounts-for-isolated-regression-testing/)

### Presentations
  - [Running your Dockerized application(s) on AWS EC2 Container Service](https://speakerdeck.com/mpas/running-your-dockerized-application-s-on-aws-ec2-container-service) by [Marco Pas](https://twitter.com/marcopas)
  - [Microservices on AWS with Weaveworks](https://www.youtube.com/watch?v=nSvpjZkmYIM)
  - [Running a Virtual World via ECS](https://www.youtube.com/watch?v=wGg_4aFOHsY) - Linden Labs on their usage of ECS
  - [Advanced Task Scheduling with AWS ECS](https://www.youtube.com/watch?v=RJZU0zZoKR8)
  - [Instacart on running microservices on Amazon ECS](https://www.youtube.com/watch?v=CtALTTjy7Qw)
  - [Building Next-Generation Applications with Amazon ECS](https://www.youtube.com/watch?v=xIc3WT6kAVw) - How Meteor Built Galaxy on Amazon ECS
  - [Amazon ECS at Coursera: A General Purpose Microservice](https://www.slideshare.net/AmazonWebServices/cmp406-amazon-ecs-at-coursera-a-generalpurpose-microservice)

### Tech Blogs

   - [Airtime](https://airtime.com) - [Microservice Continuous Integration Made Easy with AWS ECS](https://techblog.airtime.com/microservice-continuous-integration-made-easy-with-aws-ecs-10d470e31af0)
   - [Segment](https://segment.com) - [Rebuilding Our Infrastructure with Docker, ECS, and Terraform](https://segment.com/blog/rebuilding-our-infrastructure/)
   - [Nextdoor](https://nextdoor.com) - [How Nextdoor made a 10x improvement in release times with Docker and Amazon ECS](https://engblog.nextdoor.com/how-nextdoor-made-a-10x-improvement-in-release-times-with-docker-and-amazon-ecs-35aab52b726f)
   - [MapBox](https://mapbox.com) - [We switched to Amazon ECS and you won't believe what happened next](https://blog.mapbox.com/we-switched-to-amazon-ecs-and-you-wont-believe-what-happened-next-6cadbbf7282c)
   - [Wrapp - On how EC2 Container service simplified our infrastructure stack](https://medium.com/wrapp-tech/on-microservices-and-ecs-wrapp-90665d6c0339)
   - [Docker on AWS: from containerization to orchestration](http://mherman.org/blog/2017/11/16/docker-on-aws-from-containerization-to-orchestration)

### Courses

  - [Microservices with Docker, Flask, and React](https://testdriven.io/) - Learn how to build, test, and deploy microservices powered by Docker, Flask, React Amazon ECS!
