---
category: IronMQ
path: '/projects/{Project ID/queues/{Queue Name}'
title: 'Delete a Queue'
type: 'DELETE'

layout: nil
---

This call deletes a message queue and all its messages.

### Request

* **`:id`** is the id the thing to delete.
* The headers must include a **valid authentication token**.
* **The body is omitted**.

#### URL Parameters

* **Project ID**: Project the queue belongs to
* **Queue Name**: Name of the queue

### Response

```Status: 200 Deleted```
```{
    code: 200,
    "msg": "Deleted."
}```

For errors responses, see the [response status codes documentation](#response-status-codes).