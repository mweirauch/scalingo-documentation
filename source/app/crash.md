---
title: Application crash
date: 10/09/2014
tag: app, crash, recovery
category: app
---

# Application crash

For various reasons your application can terminate abruptly. Two cases of crash may happen:

## Boot errors

They are detected directly when you deploy your application, if it crashes
before binding the allocated network port, your deployment would fail.

> The former version of your application __keeps running__.

## Runtime crashes

Two situations are the most common causes of runtime crashes:

* Runtime error of your application (uncatched exception, segfault of a library/runtime)
* Temporary error of an external resource

When such an event occured, a notification is sent to you and the your collaborators for
the concerned app by email.

## Restart policy

When a runtime crash occured we automatically restart your container. If your application
stopped again in the 5 minutes after being restarted, we won't restart it directly, but
5 minutes later.

<blockquote class="info">
  <ul>
    <li>5 additional minutes are added after each crash in the 5 first minutes of runtime.</li>
    <li>A crash which occures after 5 minutes has no effect on the cool-down</li>
  </ul>
</blockquote>

> This limitation has been setup in order to avoid the situation when an
> application try to boot and crash immediately, it is to let it crash again
> and again... and again.

A limit of __12__ restart operations exist, in means that after 6 hours and 30 minutes,
your application __won't be accessible anymore__ (The last cool-off duration is 1 hour).

# What to do?

We stronly advise to look at the logs of your application using the web
dashboard or by using the [CLI tool](http://cli.scalingo.com).

According to the information gathered, you should then modify your application to
fix the issues which lead to this instability.

<blockquote class="info">
  After a successful deployment, a manual restart, or scaling of your application, we
  cancel any queued restart job, and the cool-down time after the next crash is reseted.
</blockquote>

## Need support?

Don't hesitate to contact us at [support@scalingo.com](mailto:support@scalingo.com)
