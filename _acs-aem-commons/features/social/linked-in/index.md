---
layout: acs-aem-commons_feature
title: LinkedIn Scribe Integration
description: Ease LinkedIn integration needs
date: 2013-07-25
redirect_from: /acs-aem-commons/features/linkedin-scribe.html
tags: aem-65 aem-cs
initial-release: 1.5.0
---

# Purpose

AEM 5.6.1 includes the [Scribe](https://github.com/fernandezpablo85/scribe-java) library for integration with social services using OAuth. While Scribe supports LinkedIn, it only supports this using OAuth 1.0a whereas LinkedIn is recommending that new application be written using OAuth 2.0.

# How to Use

Scribe uses a builder pattern to construct instances of `OAuthService`.

    OAuthService service = new ServiceBuilder()
        .provider(LinkedInApi20.class)
        .apiKey(key)
        .apiSecret(secret)
        .callback("http://mysite.com/linkedin")
        .build();

Scopes can be specified using the `scope()` method:

    OAuthService service = new ServiceBuilder()
        .provider(LinkedInApi20.class)
        .apiKey(key)
        .apiSecret(secret)
        .callback("http://mysite.com/linkedin")
        .scope("r_basicprofile,r_emailaddress")
        .build();

Once you have this object, you can use the `getAuthorizationUrl()`, `getAccessToken()`, and `signRequest()` methods from the `OAuthService` API.