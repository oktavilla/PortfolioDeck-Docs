---
layout: doc
title: Setting up a custom domain
---

# <span>Setting up a</span> custom domain

Registering and setting up a domain can be a bit tricky, if you don't feel comfortable dealing with this kind of stuff we recommend that you ask a tech savvy friend or [drop us an e-mail](mailto:support@portfoliodeck.com) and we'll try to help you out.

## What you need

* A domain name.
* A DNS service provider.

## Domain purchasing

For .com/.net/.org and other international domains we suggest that you use [DNSimple](https://dnsimple.com/). For Swedish domains we suggest that you use [Loopia](http://www.loopia.com/domainnames). They both offer domain registration as well as DNS services. 

If you don't like either of those there's a bunch of other DNS service providers out there and you may use whoever you prefer. 

## DNS setup

1. Go the DNS management page of your DNS service provider and select your domain name. 
2. Delete any existing A records for your domain's subdomain called ”\*”.
3. Create two new A-records for the ”\*”-subdomain: One for __95.131.248.79__ and one for __95.131.248.XYZ__. You'll probably enter this into a field called something like ”value”, ”data” or ”destination”. If you're also required to enter ”Time to live/TTL” -- use 3600 .


## Let PortfolioDeck know about your domain name

1. Click the ”Customize” button in the menu when logged in to the PortfolioDeck admin. 
2. Click the "Add a custom domain name" button.
3. Enter your domain name in the ”Custom domain” field and click "Save changes".


_Please note that after you've set up your new domain you may need to wait up to 72 hours for the change to take effect. This is just how DNS works - please be patient :)_