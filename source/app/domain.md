---
title: Custom Domain Name
date: 15/08/2014
tag: app, domain name, dns, cname
category: app
---

# Add a custom Domain Name

## Add a custom subdomain

Scalingo provides for all apps a subdomain of `scalingo.io` to access your application.
Of course, you may want to change it and use your own. This operation require different
configuration operations:

* Buy the domain name you desire from a registrar.
* Add a `CNAME` field in your DNS zone which targets `yourapp.scalingo.io.`

<blockquote class="info">
  This operation is not instant. DNS propagation can take up to days to be completely done.
</blockquote>

* Add your domain name in our dashboard:

> ![Add domain screenshot](/assets/images/add-domain.png)

## Add a root domain

Most of the registrars only allow `A` field for root domains. However `A` should target an IP. As Scalingo
is using different IP addresses for the incoming requests in order to assure the redondancy and support
server crashes, we do not recommend to target one of our frontal servers.

Some providers allow to create `ALIAS`, `ANAME` or `CNAME` field for root domains:

* DNSimple (ALIAS)
* DNS Made Easy (ANAME)
* easyDNS (ANAME)
* CloudFlare (CNAME)
* PointDNS (ALIAS)

### Note

When you add an alias, we don't do any prior verification. If you cannot add
your alias because it's already taken on Scalingo and you think you're legit
to use it, send an email to [mailto:support@scalingo.com](support.scalingo.com)
describing the problem.
