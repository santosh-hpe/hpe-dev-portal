---
title: Build your first Chatbot on HPE Private Cloud AI using Flowise and HPE MLIS
date: 2025-07-10T10:46:47.270Z
priority: ""
author: Santosh Nagaraj
authorimage: /img/santosh-picture-192.jpg
disable: false
---
In today’s AI-driven landscape, conversational interfaces are transforming how organizations interact with users and automate workflows. Building a secure, scalable, and customizable chatbot solution requires robust infrastructure and flexible AI tooling. HPE Private Cloud AI (PCAI) provides a powerful platform for deploying and managing AI workloads, while Flowise and HPE MLIS (Machine Learning Inference Software) offer the tools to rapidly build, deploy, and manage chatbots powered by large language models (LLMs).

This blog post walks you through deploying Flowise on HPE PCAI to build a modern chatbot solution. By leveraging these technologies, organizations can accelerate chatbot development, ensure data privacy, and maintain full control over their AI lifecycle.

## HPE Private Cloud AI

[HPE Private Cloud AI (HPE PCAI)](https://developer.hpe.com/platform/hpe-private-cloud-ai/home/) offers a comprehensive, turnkey AI solution designed to address key enterprise challenges, from selecting the appropriate large language models (LLMs) to efficiently hosting and deploying them. Beyond these core functions, HPE PCAI empowers organizations to take full control of their AI adoption journey by offering a curated set of pre-integrated *NVIDIA NIM* LLMs, along with a powerful suite of AI tools and frameworks for *Data Engineering*, *Analytics*, and *Data Science*.

HPE PCAI has pre-integrated NVIDIA NIM LLMs, a suite of AI tools (including HPE MLIS), and a flexible *Import Framework,* that enables organizations *to* deploy their own applications or third-party solutions like FlowiseAI. 

![](/img/importframework.jpg)

HPE Machine Learning Inference Software is a user-friendly solution designed to simplify and control the deployment, management, and monitoring of machine learning (ML) models, including LLMs, at any scale.

## What is Flowise?

[Flowise](https://flowiseai.com/) is an open source generative AI development platform for building AI Agents and LLM workflows. It provides a visual interface for designing conversational flows, integrating data sources, and connecting to various LLM endpoints. FlowiseAI’s modular architecture makes it easy to customize and extend chatbot capabilities for enterprise use cases.

- - -

## Prerequisites

* Access to an HPE PCAI environment with Import Framework enabled.
* Docker Engine (v28.1.1 or later) and Docker CLI installed.
* Helm CLI for deploying applications to Kubernetes.
* (Optional) Access to a private container registry (e.g., Harbor) for storing custom images.

- - -

## Deploying FlowiseAI and HPE MLIS on HPE PCAI

### 1. Prepare the Helm Charts

Obtain the official Helm charts for FlowiseAI and HPE MLIS. Place them in your `pcai-helm-examples` repository under the appropriate directories.

### 2. Customize Values for PCAI

Update the `values.yaml` files to configure endpoints, storage, and authentication. For example, expose FlowiseAI via Istio and set up persistent storage for conversation logs.

```yaml
# Example snippet for FlowiseAI values.yaml
ezua:
  virtualService:
    endpoint: "chatbot.${DOMAIN_NAME}"
    istioGateway: "istio-system/ezaf-gateway"

persistence:
  enabled: true
  size: 10Gi
```

For HPE MLIS, configure the model registry and inference endpoints to point to your desired LLMs.

### 3. Deploy with the Import Framework

Use the Import Framework in HPE PCAI to deploy both FlowiseAI and HPE MLIS:

```bash
helm install flowiseai ./flowiseai-helm
helm install hpe-mlis ./hpe-mlis-helm
```

Once deployed, FlowiseAI and MLIS will appear as tiles under Tools & Frameworks in the PCAI Data Science tab.

- - -

## Configuring the Chatbot

### 1. Access the FlowiseAI UI

After deployment, access FlowiseAI via the configured endpoint (e.g., `https://chatbot.ingress.pcai0104.ld7.hpecolo.net`). Log in with your admin credentials.

### 2. Build Your Chatbot Flow

Use FlowiseAI’s drag-and-drop interface to design your chatbot’s conversational flow. Integrate with HPE MLIS by adding an LLM node and configuring it to use the MLIS inference endpoint.

* **Add Data Sources:** Connect to internal databases or APIs as needed.
* **Configure LLM Node:** Set the endpoint to your deployed MLIS service.
* **Test the Flow:** Use the built-in chat preview to validate responses.

### 3. Secure and Govern Access

Leverage HPE PCAI’s RBAC and network policies to restrict access to the chatbot and underlying data sources. Use MLIS monitoring features to track model usage and performance.

- - -

## Pushing Custom Chatbot Images (Optional)

If you customize FlowiseAI or build your own chatbot container, push the image to your local Harbor registry:

```bash
docker build -t harbor.ingress.pcai0104.ld7.hpecolo.net/demo/flowiseai-chatbot:v1 .
docker push harbor.ingress.pcai0104.ld7.hpecolo.net/demo/flowiseai-chatbot:v1
```

Update your Helm chart to use the new image.

- - -

## Deploying the Chatbot Application

With FlowiseAI and MLIS configured, deploy your chatbot application to HPE PCAI using the Import Framework. The chatbot will be accessible via its endpoint, ready to serve users across your organization.

Monitor usage and performance through the FlowiseAI and MLIS dashboards. Use PCAI’s audit logs for compliance and troubleshooting.

- - -

## Conclusion

By combining FlowiseAI’s intuitive chatbot builder with HPE MLIS’s robust model management, HPE Private Cloud AI empowers organizations to rapidly develop, deploy, and govern conversational AI solutions. This integrated approach ensures data privacy, operational control, and scalability for enterprise chatbot deployments.

Stay tuned to the HPE Developer Community blog for more guides and best practices on leveraging HPE PCAI for your AI