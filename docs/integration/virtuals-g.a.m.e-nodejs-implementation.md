---
sidebar_position: 2
---

# Virtuals G.A.M.E NodeJS Implementation

## Eval Engine Plugin Javascript SDK For Virtual Game Node

### Overview

The Eval Engine Plugin is a TypeScript/JavaScript SDK for integrating Twitter functionalities with content evaluation capabilities. It's built on top of the Virtuals Protocol game framework and uses the Eval SDK for content evaluation.



### Changelog

0.1.0 [https://github.com/game-by-virtuals/game-node/pull/19](https://github.com/game-by-virtuals/game-node/pull/19)&#x20;



Features

* All evaluation results of reply tweets are logged in EvalEngine
* The evaluation results are then piped into the reply tweet function to determine whether to post the tweet or not

![agent-logs.png](/assets/agent-logs.png)


### Installation

Setup Chromia Private Key: [Guide](../setup-chromia-account.md)

To install the plugin, use npm or yarn:

```bash
npm install @virtuals-protocol/game-eval-engine-plugin
```

or

```bash
yarn add @virtuals-protocol/game-eval-engine-plugin
```



### Key Components

#### TwitterPlugin

The main class that handles Twitter integration with content evaluation. It provides several key capabilities:

* Tweet posting and interaction
* Content evaluation before posting
* Score-based filtering
* Twitter metrics tracking

#### Core Features

1. **Content Evaluation**

* Uses

EvaClient

for evaluating tweet content

* Implements threshold scoring system
* Validates content before posting

2. **Twitter Functions**

* Search tweets
* Post tweets
* Reply to tweets
* Like tweets
* Quote tweets

### Usage Example

```typescript
import TwitterPlugin from "@virtuals-protocol/game-eval-engine-plugin";
import { initEvalClient } from "./evalEngine";

// Initialize the eval client
const evalClient = await initEvalClient(PRIVATE_KEY);

// Create Twitter plugin instance
const twitterPlugin = new TwitterPlugin({
  credentials: {
    apiKey: "YOUR_API_KEY",
    apiSecretKey: "YOUR_API_SECRET",
    accessToken: "YOUR_ACCESS_TOKEN", 
    accessTokenSecret: "YOUR_ACCESS_TOKEN_SECRET"
  },
  thresholdScore: 0.5,
  evalClient
});

// Get worker instance
const worker = twitterPlugin.getWorker();
```

### Available Functions

#### 1. Search Tweets

```typescript
searchTweetsFunction({
  query: "search query"
})
```

#### 2. Reply to Tweet

```typescript
replyTweetFunction({
  tweet_id: "123456",
  reply: "Reply content",
  reply_reasoning: "Reasoning for reply"
})
```

#### 3. Post Tweet

```typescript
postTweetFunction({
  tweet: "Tweet content",
  tweet_reasoning: "Reasoning for tweet"
})
```

#### 4. Like Tweet

```typescript
likeTweetFunction({
  tweet_id: "123456"  
})
```

#### 5. Quote Tweet

```typescript
quoteTweetFunction({
  tweet_id: "123456",
  quote: "Quote content"
})
```

### Configuration

The plugin accepts the following configuration options:

```typescript
interface ITwitterPluginOptions {
  id?: string;
  name?: string; 
  description?: string;
  credentials: {
    apiKey: string;
    apiSecretKey: string;
    accessToken: string;
    accessTokenSecret: string;
  };
  thresholdScore?: number;
  evalClient: EvalClient;
}
```

### Error Handling

The plugin implements comprehensive error handling through

ExecutableGameFunctionResponse

with appropriate status codes and error messages.

### Dependencies

* @virtuals-protocol/game
* eval-engine-sdk
* twitter-api-v2

### License

MIT License