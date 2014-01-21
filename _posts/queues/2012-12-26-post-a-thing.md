---
category: IronMQ
path: '/projects/{Project ID}/queues/{Queue Name}/messages'
title: 'Add Messages to a Queue'
type: 'POST'

layout: nil
---

This call adds or pushes messages onto the queue.

### Request

#### URL Parameters

* **Project ID**: The project these messages belong to.
* **Queue Name**: The name of the queue. If the queue does not exist, it will be created for you.

#### Message Object

Multiple messages may be added in a single request, provided that the messages should all be added to the same queue. Each message object should contain the following keys:

##### Required

* **body**: The message data

##### Optional

* **timeout**: After timeout (in seconds), item will be placed back onto queue. You must delete the message from the queue to ensure it does not go back onto the queue. Default is 60 seconds. Minimum is 30 seconds, and maximum is 86,400 seconds (24 hours).
* **delay**: The item will not be available on the queue until this many seconds have passed. Default is 0 seconds. Maximum is 604,800 seconds (7 days).
* **expires_in**: How long in seconds to keep the item on the queue before it is deleted. Default is 604,800 seconds (7 days). Maximum is 2,592,000 seconds (30 days).

```{
  "messages": [
    {
      "body": "This is my message 1."
    },
    {
      "body": "This is my message 2.",
      "timeout": 30,
      "delay": 2,
      "expires_in": 86400
    }
  ]
}```

### Response

**If succeeds**, returns the created thing.

```Status: 201 Created```
```{
  "ids": ["message 1 ID", "message 2 ID"],
  "msg": "Messages put on queue."
}```

For errors responses, see the [response status codes documentation](#response-status-codes).
