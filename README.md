# Cognitive Services Workshop

This folder contains hands-on labs introducing some of the tools available in Azure and in [Azure Cognitive Services](https://azure.microsoft.com/services/cognitive-services/) for building intelligent bots and applications backed by AI and machine learning. 

> NOTE: most of the lab content is hosted in remote Git repositories. Be sure to bookmark or keep this page open.

# Prerequisites

In order to complete these labs, you will need the following:

* An Azure subscription. If you do not yet have one,
navigate to <https://azure.microsoft.com>; click the [Start Free] button and
follow the instructions to sign up for a free Azure trial.

* A text editor. We recommend [Visual Studio Code](https://code.visualstudio.com/), because it
is free, lightweight, and will run on Windows , MacOS, or Linux. You can
download Visual Studio Code at <https://code.visualstudio.com/>. But feel free
to use any editor with which you are comfortable.

* The [Node.js](https://nodejs.org/) JavaScript runtime. Go to the [download page](https://nodejs.org/en/download/) to get the Node.js version for your operating system.

# Initial Setup

Before creating any other Azure services, it would be a good idea to [create a Resource Group](https://docs.microsoft.com/en-us/azure/azure-resource-manager/resource-group-template-deploy-portal#create-resource-group) to store those services in. This will allow you to clean up easily after the lab, by simply deleting the Resource Group and all the services within.

# Labs

Lab | Scenario | Technology/Language
--- | -------- | -------------------
[Face](./Lab1/Cognitive%20Services%20Labs-Lab%2001-1.md) | Use the Face API to detect people and understand emotions. | [Face](https://azure.microsoft.com/en-us/services/cognitive-services/face/)<br>JavaScript, Python
[Custom Vision Service](https://github.com/Microsoft/computerscience/blob/master/Labs/AI%20and%20Machine%20Learning/Custom%20Vision%20Service/Custom%20Vision%20Service.md) | Train a neural network to recognize famous paintings. Then build a Node.js app that uses the network to identify the artists of paintings that you upload. | [Custom Vision Service](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/)<br>JavaScript 
[Video Indexer](https://github.com/Microsoft/computerscience/blob/master/Labs/AI%20and%20Machine%20Learning/Video%20Indexer/Video%20Indexer.md) | Index a collection of videos and extract insights such as people in the videos, topics discussed in the videos, and video transcripts. Then deploy a Node.js app that makes video content searchable. | [Video Indexer](https://azure.microsoft.com/services/cognitive-services/video-indexer/)<br>JavaScript 
[Azure Bot Service](https://github.com/Microsoft/computerscience/blob/master/Labs/AI%20and%20Machine%20Learning/Azure%20Bot%20Service/Azure%20Bot%20Service.md) | Build an intelligent chat bot using JavaScript and Node.js, deploy it to Azure, and converse with it using Skype. | [Azure Bot Service](https://azure.microsoft.com/services/bot-service/)<br>[Microsoft QnA Maker](https://qnamaker.ai/)<br>JavaScript 
[LUIS](https://github.com/Microsoft/computerscience/blob/master/Labs/AI%20and%20Machine%20Learning/LUIS/LUIS.md) | Build a language-understanding model with the Microsoft Language Understanding Intelligent Service (LUIS). Then deploy a bot that uses the model to respond to commands such as "Get the latest news about Microsoft." | [Microsoft LUIS](https://azure.microsoft.com/services/cognitive-services/language-understanding-intelligent-service/)<br>JavaScript 