---
layout: page
title: RESTful APIs
permalink: /restfulapis/
---

## Best Practices in Designing RESTful APIs

### Require versioning in Accepts header

```bash
Accept: application/vnd.heroku+json; version=3
```

### Accept serialized JSON in request bodies

Accept serialized JSON on `PUT`/`PATCH`/`POST` request bodies, either instead of or in addition to form-encoded data.

```bash
$ curl -X POST https://service.com/apps \
    -H "Content-Type: application/json" \
    -d '{"name": "demoapp"}'

{
  "id": "01234567-89ab-cdef-0123-456789abcdef",
  "name": "demoapp",
  "owner": {
    "email": "username@example.com",
    "id": "01234567-89ab-cdef-0123-456789abcdef"
  },
  ...
}
```

### Use consistent path formats

#### Resource names

Use the plural version of a resource name unless the resource in question is a singleton within the system (for example, in most systems a given user would only ever have one account). This keeps it consistent in the way you refer to particular resources.

#### Actions

Prefer endpoint layouts that don’t need any special actions for individual resources. In cases where special actions are needed, place them under a standard actions prefix, to clearly delineate them:

```bash
/resources/:resource/actions/:action
```

### Downcase paths and attributes

* Use downcased and dash-separated path names, for alignment with hostnames.
* Downcase attributes, but use underscore separators so that attribute names can be typed without quotes in JavaScript, e.g.:

```js
"service_class" : "first"
```

### Support non-id dereferencing for convenience

```bash
$ curl https://service.com/apps/{app_id_or_name}
$ curl https://service.com/apps/97addcf0-c182
$ curl https://service.com/apps/www-prod
```

### Minimize path nesting

Limit nesting depth by preferring to locate resources at the root path. Use nesting to indicate scoped collections

### Responses

#### Return appropriate status codes

Refer to the [https://tools.ietf.org/html/rfc7231#section-6](HTTP response code spec) for guidance on status codes for user error and server error cases.

#### Provide full resources where available

Provide the full resource representation (i.e. the object with all attributes) whenever possible in the response.

#### Provide resource (UU)IDs

Give each resource an id attribute by default. Render UUIDs in downcased 8-4-4-4-12 format, e.g.:

```js
"id": "01234567-89ab-cdef-0123-456789abcdef"
```
#### Provide standard timestamps

Provide created_at and updated_at timestamps for resources by default, e.g:

```js
{
  // ...
  "created_at": "2012-01-01T12:00:00Z",
  "updated_at": "2012-01-01T13:00:00Z",
  // ...
}
```

#### Use UTC times formatted in ISO8601

```js
"finished_at": "2012-01-01T12:00:00Z"
```

#### Nest foreign key relations

Use:

```js
{
  "name": "service-production",
  "owner": {
    "id": "5d8201b0..."
  },
  // ...
}
```

Instead of:

```js
{
  "name": "service-production",
  "owner_id": "5d8201b0...",
  // ...
}
```

#### Generate structured errors

Generate consistent, structured response bodies on errors. Include a machine-readable error id, a human-readable error message, and optionally a url pointing the client to further information about the error and how to resolve it

```
HTTP/1.1 429 Too Many Requests
{
  "id":      "rate_limit",
  "message": "Account reached its API rate limit.",
  "url":     "https://docs.service.com/rate-limits"
}
```

#### Show rate limit status

Rate limit requests from clients to protect the health of the service and maintain high service quality for other clients. You can use a [http://en.wikipedia.org/wiki/Token_bucket](token bucket algorithm) to quantify request limits.

#### Keep JSON minified in all responses

Extra whitespace adds needless response size to requests, and many clients for human consumption will automatically "prettify" JSON output. It is best to keep JSON responses minified.

You may consider optionally providing a way for clients to retrieve more verbose response, either via a query parameter (e.g. `?pretty=true`) or via an Accept header param (e.g. `Accept: application/vnd.heroku+json; version=3; indent=4;`).

### Artifacts

* Provide a machine-readable schema to exactly specify your API. Use [https://github.com/interagent/prmd](prmd) to manage your schema, and ensure it validates with prmd verify.
* Provide human-readable docs
* Provide executable examples
* Describe stability - See the [https://devcenter.heroku.com/articles/api-compatibility-policy](Heroku API compatibility policy) for a possible stability and change management approach.

Reference:
[https://github.com/interagent/http-api-design](https://github.com/interagent/http-api-design)