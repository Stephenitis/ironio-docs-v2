---
category: IronMQ
path: '/projects/{Project ID}/queues/{Queue Name}'
title: 'Update a Queue'
type: 'POST'

layout: nil
---

This allows you to change the properties of a queue including setting subscribers and the push type if you want it to be a
push queue.


### Request

#### URL Parameters

* **Project ID**: Project the queue belongs to
* **Queue Name**: Name of the queue. If the queue does not exist, it will be created for you.

#### Body Parameters

##### Optional

The following parameters are all related to Push Queues.

* **subscribers**: An array of subscriber hashes containing a required "url" field and an optional "headers" map for custom headers. This set of subscribers will replace the existing subscribers. See [Push Queues](/mq/reference/push_queues/) to learn more about types of subscribers. To add or remove subscribers, see the <a href="#add_subscribers_to_a_queue">add subscribers endpoint</a> or the <a href="#remove_subscribers_from_a_queue">remove subscribers endpoint</a>. The maximum is 64kb for JSON array of subscribers' hashes. See below for example JSON.
* **push_type**: Either `multicast` to push to all subscribers or `unicast` to push to one and only one subscriber.
Default is `multicast`. To revert push queue to reqular pull queue set `pull`.
* **retries**: How many times to retry on failure. Default is 3. Maximum is 100.
* **retries_delay**: Delay between each retry in seconds. Default is 60.
* **error_queue**: The name of another queue where information about messages that can't be delivered after retrying `retries` number of times will be placed. Pass in an empty string to disable error queues. Default is disabled. See [Push Queues](/mq/reference/push_queues/) to learn more.

```{
  "push_type":"multicast",
   "subscribers": [
     {"url": "http://mysterious-brook-1807.herokuapp.com/ironmq_push_1"},
     {
        "url": "http://mysterious-brook-1807.herokuapp.com/ironmq_push_2",
        "headers": {"Content-Type": "application/json"}
     }
   ]
}```

### Response

Sends back a collection of things.

```Status: 200 OK```
```{
  "id":"50eb546d3264140e8638a7e5",
  "name":"pushq-demo-1",
  "size":7,
  "total_messages":7,
  "project_id":"4fd2729368a0197d1102056b",
  "retries":3,
  "push_type":"multicast",
  "retries_delay":60,
  "subscribers":[
    {"url":"http://mysterious-brook-1807.herokuapp.com/ironmq_push_1"},
    {"url":"http://mysterious-brook-1807.herokuapp.com/ironmq_push_2", "headers": {"Content-Type": "application/json"}}
  ]
}```

For errors responses, see the [response status codes documentation](#response-status-codes).