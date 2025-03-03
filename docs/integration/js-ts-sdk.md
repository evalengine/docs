---
sidebar_position: 3
---

# JS/TS SDK

A JavaScript SDK for interacting with Eval Engine, a transparent evaluation system built on Chromia blockchain.

[eval-engine-sdk npm](https://www.npmjs.com/package/eval-engine-sdk)

### Installation

```sh
npm install eval-engine-sdk
```

### Core Components

#### Requirements

* Node.js >= 18.0.0 (for native fetch support)
* [Chromia Private Key](https://eval-engine.gitbook.io/eval-engine/setup-chromia-account)

#### Eval Client

The main client used by end users to interact with the Eval Engine. It requires a Chromia private key for initialization.

View [examples/user\_demo.ts](https://github.com/evalengine/eval-sdk/blob/main/js_sdk/examples/user_demo.ts) for full implementation

```ts
import { EvalClient, CHROMIA_CHAIN } from 'eval-engine-sdk';

const evalClient = await EvalClient.init(
    PRIVATE_KEY,
    CHROMIA_CHAIN.MAINNET,
    {
        url: "https://api.evalengine.ai/api",
        prefix: "EVA",
        pub: "YOUR_ENGINE_PUBLIC_KEY"
    }
);
```

Key Methods:

* `getEngine()`: Retrieves engine information
* `signEvaluateTweetRequest(inputTweet, outputTweet)`: Signs an evaluation request
* `submitEvaluateTweetRequest(txHash)`: Submits a signed evaluation request

To use it, simply:

```ts
const input = "Input tweet here";
const reply = "Replied tweet here";
const txHash = await evalClient.signEvaluateTweetRequest(input, reply);
console.log("txHash", txHash);
const response = await evalClient.submitEvaluateTweetRequest(txHash);
console.log("response", JSON.stringify(response, null, 2));
```

#### Engine Client

> This is the server implementation of Engine

View [examples/engine\_server\_demo.ts](https://github.com/evalengine/eval-sdk/blob/main/js_sdk/examples/engine_server_demo.ts) for full implementation

```ts
import { EngineClient, CHROMIA_CHAIN } from 'eval-engine-sdk';

const engine = await EngineClient.init(ENGINE_PRIVATE_KEY, CHROMIA_CHAIN.MAINNET);
```