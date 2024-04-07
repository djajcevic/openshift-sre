# Day 1

## Cluster Management Basics

### Environment Setup

...

### Exercise 1

1. Get OC CLI tool from `<your-lab-cluster-url>/command-line-tools` URL and extract it
2. Create `joe` project
3. Using `oc` tool, figure out how to create a user and create user `alice` and `<yourusername>`
4. [Using RBAC](https://docs.openshift.com/container-platform/4.15/authentication/using-rbac.html) make `alice` admin of `joe` project
   - impersonate `alice` to make sure she can administrate `joe` project
   - follow through the rest of the examples
     - Viewing cluster roles and bindings
     - Viewing local roles and bindings
     - Adding roles to users
     - Creating a local role
     - Creating a cluster role
     - Local role binding commands
     - Cluster role binding commands
     - Creating a cluster admin
6. [Working with projects](https://docs.openshift.com/container-platform/4.15/applications/projects/working-with-projects.html)
7. [Quotas per project](https://docs.openshift.com/container-platform/4.15/applications/quotas/quotas-setting-per-project.html)


