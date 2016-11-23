---
layout: post
title:  "Step by step guide how to build a Bot with Microsoft Bot Framework"
date:   2016-11-23 08:00
categories: Bots
permalink: /step-by-step-guide-how-to-build-a-bot-with-microsoft-bot-framework
---

# Introduction

In this article I'm going to show you how to build a simple bot using [https://dev.botframework.com/](https://dev.botframework.com/) platform and its SDK.
Client Libraries for the Bot State REST API:

1. [Bot Builder for C#](https://docs.botframework.com/en-us/csharp/builder/sdkreference/)
2. [Bot Builder for Node.js](https://docs.botframework.com/en-us/node/builder/overview/)
3. [Generate your own from the State API Swagger file](https://raw.githubusercontent.com/Microsoft/BotBuilder/master/CSharp/Library/Microsoft.Bot.Connector/Swagger/StateAPI.json)

C# language and its SDK is a choice in this artcle.  
[wit.ai](https://wit.ai) going to be used to understand natural language from users. [luis.ai](https://www.luis.ai/) from Microsoft can be considered as an alternative for [wit.ai](https://wit.ai). Having tried [luis.ai](https://www.luis.ai/), I decided to go with [wit.ai](https://wit.ai), because of it's simplicity, some more reach functionality and Ukrainian language support. Definitely try [luis.ai](https://www.luis.ai/), since it's being improved permanently, but in this article only [wit.ai](https://wit.ai) is the way to go :)

# Project creation

# References

- [https://dev.botframework.com](https://dev.botframework.com)
- [Getting started with the Connector](https://docs.botframework.com/en-us/csharp/builder/sdkreference/gettingstarted.html)
- [wit.ai](https://wit.ai/)
- [luis.ai](https://www.luis.ai/)