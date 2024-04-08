# Day 1

## Cluster Management Basics

### Environment Setup

...

### Exercise 1.1

1. Get OC CLI tool from `<your-lab-cluster-url>/command-line-tools` URL and extract it
2. Follow [documentation](https://docs.openshift.com/container-platform/4.15/cli_reference/openshift_cli/getting-started-cli.html) and login to cluster
3. Create `joe` project via [Web Console](https://docs.openshift.com/container-platform/4.15/applications/projects/working-with-projects.html#creating-a-project-using-the-web-console_projects)
4. Using `oc` tool, figure out how to create a user and create user `alice` and `<yourusername>`
5. Examine [Using RBAC](https://docs.openshift.com/container-platform/4.15/authentication/using-rbac.html) documentation and make `alice` admin of `joe` project
   - impersonate `alice` to make sure she can administrate `joe` project
   - follow through the rest of the examples from the above documentation
     - Viewing cluster roles and bindings
     - Viewing local roles and bindings
     - Adding roles to users
     - Creating a local role
     - Creating a cluster role
     - Local role binding commands
     - Cluster role binding commands
     - Creating a cluster admin
6. Go through the rest of the examples from [Working with projects](https://docs.openshift.com/container-platform/4.15/applications/projects/working-with-projects.html) documentation
   - Creating a project
      - Creating a project by using the CLI
    - Viewing a project
      - Viewing a project using the CLI
    - Providing access permissions to your project using the Developer perspective
    - Checking the project status
      - Checking project status by using the web console
      - Checking project status by using the CLI
    - Deleting a project
      - Deleting a project by using the web console
      - Deleting a project by using the CLI
     
### Exercise 1.2

1. [Setting Limit Range](https://docs.openshift.com/container-platform/4.15/nodes/clusters/nodes-cluster-limit-ranges.html)
    - Creating a Limit Range
    - Viewing a limit
    - Deleting a Limit Range
3. [Quotas per project](https://docs.openshift.com/container-platform/4.15/applications/quotas/quotas-setting-per-project.html)
    - Creating a quota
      - Creating object count quotas
      - Setting resource quota for extended resources
    - Viewing a quota
3. Clone repository [Project Snake](https://github.com/OperatingOpenShift/s3e)
4. Go to `highscore/backup` directory and invoke all commands from `setup.sh` script
   ```pwsh
   oc apply -f 01-namespace.yaml
   oc project arcade
   oc new-app --name=game --context-dir=game https://github.com/NautiluX/s3e
   oc new-app --name=highscore --context-dir=highscore https://github.com/NautiluX/s3e
   $DOMAIN=$(oc get ingresses.config.openshift.io  cluster -o jsonpath='{.spec.domain}')
   oc expose svc game --path=/s3e --hostname=arcade.$DOMAIN
   oc expose svc highscore --path=/highscore --hostname=arcade.$DOMAIN
   oc apply -f 02-persistentvolumeclaim.yaml
   oc apply -f 03-deployment.yaml
   ```
5. After everyting is up, play a game and examine high scores
6. Introduce a namespace memory quota of 10MB and increase number of instances 3 of each deployment (are applications starting?)
7. Configure cpu and memory requests on `game` deployment (was it able to rollout?)
