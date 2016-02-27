# cluster-logger
Get your worker child processes logs to show up in Cloudwatch or Papertrail when using cluster in NodeJS

#### Getting Started

Install `cluster-logger`

  npm install cluster-logger

`require` it in your cluster script.

```js
require('cluster-logger')
```

You're done.

#### What is this, why don't I need it?

This is a very simple solution to a very specific problem.
You are using the new `cluster` module in NodeJS.  And you find that the logs of your spawned processes are not appearing in your
production log tracker.

This module simply proxies `console.log` and `console.error` to `process.send({ type: 'log', message: ... })`.
It also creates a listener in the master process, to receive those logs and spit them out in the main stdio stream.
