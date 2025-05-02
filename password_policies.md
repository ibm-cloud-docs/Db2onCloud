---

copyright:
  years: 2014, 2021
lastupdated: "2025-05-02"

keywords: db2, Db2 on Cloud, bring your own key, byok, crypto-shredding, kyok, keep your own key

subcollection: Db2onCloud

---


{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:important: .important}
{:note: .note}
{:deprecated: .deprecated}
{:pre: .pre}

# Password Policy Options

The following user password policy options are supported. These can be configured via the relevant user management commands. Duration-based values are specified in **minutes** (converted internally from seconds).

> **Note**: If not provided, the following enforced minimums apply:
>
> - `minimum_length`: 8 characters
> - `max_attempts`: 3 attempts

---

## Supported Policy Options

### `minimum_length`

Specifies the minimum number of characters required for a valid password.

### `max_attempts`

Defines the maximum number of failed login attempts allowed before the user is locked out.

### Password Expiration

Specifies the number of days after which a password will expire and require the user to set a new one.

### Lock Duration

Specifies the duration (in minutes) a user remains locked out before being automatically unlocked, based on the time the account was locked.

### Password Failure Interval

Defines the time window (in minutes) for tracking failed login attempts. If the user's last failed attempt falls outside this interval, the failure count is reset.

### Password History

Specifies the number of previously used passwords that cannot be reused by the user. Previously used passwords are not tracked unless `Password History` is enabled.
