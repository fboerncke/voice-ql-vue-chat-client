<a href= "https://prototypefund.de/project/voice-ql-datentabellen-mit-gesprochener-sprache-barrierefrei-erkunden/"><img src="./resources/assets/voice-ql-ring.png" width="40%" height="40%" align="right"></a>

# Voice-QL - Web Client - Chat Widget

## Introduction

This code in this repository is part of the ["Voice QL" project](https://github.com/fboerncke/voice-ql) and requires two other services to be up and running when you want to run it (see installation instructions below).

The main setup and architecture has been cloned from the Jovo ChatBot example which can be found here: https://github.com/jovotech/jovo-starter-web-chatwidget

You can use this Web Client to communicate with a database via a ChatBot like interface using natural language commands.

## Look and feel

After launch in a browser you can use a chat interface to type in German voice commands which will then be executed by the Voice-QL backend.

The bigger window will show the auto generated SQL statements that have been build on the fly to answer your request. The following screen shot shows you the look and feel:

[![Chatbot](./resources/screenshot-web-client.png)](https://www.bmbf.de/)

## Setup for test environment

How to setup:

1. **Preparation**: Start **Snips NLU** as described here: https://github.com/fboerncke/voice-ql#setup--installation

2. **Preparation**: Start **Voice-QL** as described here: https://github.com/fboerncke/voice-ql#setup--installation

   The chatbot will use (1) and (2) as backend.

3. Checkout, build and start the chatbot:

   ```
   mkdir voice-ql-vue-chatbot
   git clone ...
   npm install
   npm run serve
   ```

4. If you experience problems when launching and see error messsages related to SSL this may be because of a newer node version. The following environment setting should help you in that case:

   ```
   export NODE_OPTIONS=--openssl-legacy-provider
   ```

   Then run `npm run serve` again.

5. Now use your local browser and navigate to the address shown in the console window, e.g. `http://localhost:8080/` and follow the instructions on the screen.

## App

You can host your Jovo app on almost any platform, whether you choose a hosting provider or to build your own Node.js-based HTTP server. Here are a few examples:

- [AWS Lambda](https://www.jovo.tech/marketplace/server-lambda)
- [Express](https://www.jovo.tech/marketplace/server-express)

## About Jovo

Jovo is the most popular development framework for voice, including platforms like Alexa, Google Assistant, and the web.

- [Jovo Website](https://jovo.tech/)
- [Documentation](https://jovo.tech/docs/)
- [Marketplace](https://www.jovo.tech/marketplace/)
- [Twitter](https://twitter.com/jovotech/)
- [Forum](https://community.jovo.tech/)

## Acknowledgements

This project receives funding from the [German Federal Ministry of Education and Research](https://www.bmbf.de/) (FKZ 01IS22S30)

[![Logo Bundesministerium für Bildung und Forschung](./resources/assets/logo-bmbf.svg)](https://www.bmbf.de/)
&nbsp; &nbsp;
[![Logo Open Knowledge Foundation](./resources/assets/logo-okfn.svg)](https://okfn.de)
&nbsp; &nbsp;
[![Logo Prototype Fund](./resources/assets/PrototypeFund_Logo_smallest.svg)](https://prototypefund.de/)

The Prototype Fund is a project of the Open Knowledge Foundation Germany, funded by the German Federal Ministry of Education and Research (BMBF).
