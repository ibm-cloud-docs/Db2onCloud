---

copyright:
  years: 2014, 2021
lastupdated: "2025-05-02"

keywords: db2, Db2 on Cloud, bring your own key, byok, crypto-shredding, kyok, keep your own key

subcollection: Db2onCloud

---

<!-- Attribute definitions -->
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

Defines the time window (in minutes) for tracking failed login attempts. If the user's last failed attempt falls outside this interval, the failure count is reset. The failure count does not reset if the user is locked out and requires admin intervention to unlock the user.

### Password History

Specifies the number of previously used passwords that cannot be reused by the user. Previously used passwords are not tracked unless `Password History` is enabled.

<!-- ### **User Management Changes**

### `UM_GET_USERS`

An additional field for password expiration has been added to the user table output.

**Example Output:**

| USERNAME  | IBMID | ROLE | EMAIL | GROUP | LOCKED | POLICYNAME | PWDEXPIRY | GRACEDUE | GRACESLEFT |
|-----------|-------|------|-------|-------|--------|-------------|-----------|----------|-------------|
| testuser  | -     | -    | -     | bluusers | 0    | mayo        | 2024-12-16T19:24:38 | 2024-12-21T19:24:38 | 3 |

---

### `UM_MODIFY_USER`

Adds a new optional field `policyname` to assign a new policy to an existing user.

**Example:**

```bash
$ db2 "call um_modify_user(username => 'testuser3', policyname => 'maxpolicy')"
# Return Status = 0
```

### `UM_GET_POLICIES`

Returns a list of all defined password policies and their respective settings.

**Example Output:**

| POLICYNAME | MINLENGTH | LOCKDURATION | MAXATTEMPTS | FAILURECOUNTINTERVAL | PWDHISTORY | PWDEXPIRATIONTIME |
|------------|-----------|--------------|-------------|-----------------------|------------|--------------------|
| default    | 22        | 10           | 5           | 3                     | 3          | 30                 |
| mayo       | -         | -            | -           | -                     | -          | 10                 |

---

### `UM_CREATE_POLICY`

Creates a new password policy. You only need to specify the attributes you wish to define.

**Examples:**

```bash
$ db2 "call um_create_policy(name => 'testpolicy', pwd_expiration_time => 30)"

  Return Status = 0
```

```bash
$ db2 "call um_create_policy(name => 'maxpolicy', min_length => 8, lock_duration => 2, max_attempts => 10, pwd_count_interval => 30, pwd_history => 5, pwd_expiration_time => 15)"

  Return Status = 0
```

### `UM_MODIFY_POLICY`

Modifies the specified attributes of an existing password policy. Only the attributes to be changed need to be specified.

```bash
$ db2 "call um_modify_policy(name => 'testpolicy', min_length => 10)"

  Return Status = 0
```

### `UM_DELETE_POLICY`

Deletes an existing policy. If there are users with the policy you want to delete, those users will have their policies reverted back to the default policy defined by us in the `users.json`

```bash
$ db2 "call um_delete_policy('testpolicy');"

  Return Status = 0
``` -->
