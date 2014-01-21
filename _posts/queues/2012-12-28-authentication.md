---
path: '/login'
title: 'Authenticate'

layout: nil
---

### Authentication
IronMQ uses OAuth2 tokens to authenticate API requests. All methods require authentication unless specified otherwise. You can find and create your API tokens [in the HUD](https://hud.iron.io/tokens). To authenticate your request, you should include a token in the Authorization header for your request or in your query parameters. Tokens are universal, and can be used across services.

Note that each request also requires a Project ID to specify which project the action will be performed on. You can find your Project IDs [in the HUD](https://hud.iron.io). Project IDs are also universal, so they can be used across services as well.

**Example Authorization Header**:  
Authorization: OAuth abc4c7c627376858

**Example Query with Parameters**:  
GET https://<span class="variable host">mq-aws-us-east-1</span>.iron.io/1/projects/<span class="variable project_id">{Project ID}</span>/queues?oauth=abc4c7c627376858

Notes:

* Be sure you have the correct case, it's **OAuth**, not Oauth.
* In URL parameter form, this will be represented as:
        `?oauth=abc4c7c627376858`

For errors responses, see the [response status codes documentation](#response-status-codes).