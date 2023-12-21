# Minimal LLM Finetune Launch Job

This repo implements a minimal example of a Launch Job for finetuning a LLM model using the HF ecosystem.

### Create a Docker Image

First, let's create a Docker image called `train` with the docker build command:

```
docker build -f ./Dockerfile.train -t train:v0 .
```

### Create a Launch Job

We'll create a launch job with the W&B CLI with the following code snippet:

```
wandb job create --project tinyllama --entity <your_entity> --name train image train:v0
```

### Create a Launch Queue

Head on to [Launch]() and create a new Docker queue in your entity. This will give you the command to start a launch agent that you can trigger on your local machine (same one where you built the docker image). Don't forget to setup OPENAI_API_KEY on that machine and pass info to the queue to pick it up:

![Launch Queue Configuration](image.png)

### Run the Launch Agent

