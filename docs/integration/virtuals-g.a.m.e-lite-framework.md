---
sidebar_position: 1
---

# Virtuals G.A.M.E lite Framework

### Prerequisite

* G.A.M.E Lite environment configured
* Valid JWT Token (high-frequency rotation)
* API Key from G.A.M.E Lite

### Step by step guide

<iframe height="500" width="100%" src="https://www.youtube.com/embed/NCQyOoDBCKY" frameborder="0" allowfullscreen></iframe>

#### 1. Agent Configuration

* Go to [https://app.virtuals.io/](https://app.virtuals.io/)
* Login → Agent dashboard
* Configure Sandbox mode (to get JWT token)

#### 2. JWT Integration

Base URL transformation:

```
FROM: https://game-lite.virtuals.io/?token=xyz
TO:   https://evalengine.ai?token=xyz
```

#### 3. API Authentication

* Grab API Key from G.A.M.E Lite
* Drop it in EvalEngine settings

### Integration Complete

You can now simulate your ai agent on EvalEngine

![tweet-evaluation-report](/assets/tweet-evaluation-report.jpeg)



