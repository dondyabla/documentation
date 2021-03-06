---
title: Webhooks
layout: page
tags:
  - webhooks
  - integrations
category: Getting Started
redirect_from:
  - /integrations/webhooks/
---
## Setup

Go to the _Notification_ settings of your project and enter the HTTP endpoint of the service you want to notify.

![Webhooks]({{site.baseurl}}/images/integrations/webhooks.png)

## Payload

We send you a POST request containing the following build data

```json
{
  "build": {
    "build_url":"https://www.codeship.com/projects/10213/builds/973711",
    "commit_url":"https://github.com/codeship/docs/
                  commit/96943dc5269634c211b6fbb18896ecdcbd40a047",
    "project_id":10213,
    "build_id":973711,
    "status":"testing",
    # PROJECT_FULL_NAME IS DEPRECATED AND WILL BE REMOVED IN THE FUTURE
    "project_full_name":"codeship/docs",
    "project_name":"codeship/docs",
    "commit_id":"96943dc5269634c211b6fbb18896ecdcbd40a047",
    "short_commit_id":"96943",
    "message":"Merge pull request #34 from codeship/feature/shallow-clone",
    "committer":"beanieboi",
    "branch":"master"
  }
}
```

The _status_ field can have one of the following values:

- `testing` for newly started build
- `error` for failed builds
- `success` for passed builds
- `stopped` for stopped builds
- `waiting` for waiting builds
- `ignored` for builds ignored because the account is over the monthly build limit
- `blocked` for builds blocked because of excessive resource consumption
- `infrastructure_failure` for builds which failed because of an internal error on the build VM
