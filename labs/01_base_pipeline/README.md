# Create a base pipeline

This folder holds the files for the lab _Create a Base Pipeline_ which is part of the **IBM-CD0215EN-Skills Network Introduction to CI/CD** course.

## Prerequisites

- Kubernetes cluster
- Tekton Pipelines installed on the cluster

## Applying Tekton Tasks

First, apply the Tekton Tasks to your cluster.

`kubectl apply -f tasks.yaml`

## Applying Tekton Pipeline

Next, apply the Tekton Pipeline to your cluster.

`kubectl apply -f pipeline.yaml`

## Run the pipeline

Finally, Run the pipeline using the Tekton CLI:

```
tkn pipeline start cd-pipeline \
    --showlog \
    -p repo-url="https://github.com/ibm-developer-skills-network/wtecc-CICD_PracticeCode.git" \
    -p branch="main"
```

The pipeline will run and you will see the output in the terminal like this:

```
PipelineRun started: cd-pipeline-run-wvfzx
Waiting for logs to be available...
[clone : checkout] Cloning into 'wtecc-CICD_PracticeCode'...

[lint : echo-message] Calling Flake8 linter...

[tests : echo-message] Running unit tests with PyUnit...

[build : echo-message] Building image for https://github.com/ibm-developer-skills-network/wtecc-CICD_PracticeCode.git ...

[deploy : echo-message] Deploying main branch of https://github.com/ibm-developer-skills-network/wtecc-CICD_PracticeCode.git ...
```
