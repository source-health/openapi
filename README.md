# Catalyst's OpenAPI Specification

This repository contains [OpenAPI specifications][openapi] for the Catalyst's API.

Files can be found in the `openapi/` directory:

* `spec3.{json,yaml}:` OpenAPI 3.0 spec matching the public Catalyst API.
    * Our OpenAPI specification includes vendor specific extensions that we use to
      generate documentation and SDKs.

We currently only support the OpenAPI 3.0 specification format. Other versions may be
added in the future and the file name in the openapi directory will be updated to reflect
the version to which it refers.

## Vendor Extensions

The specification ships with a few vendor-specific fields to help represent
information in ways that are difficult in OpenAPI by default.

### `x-expandable`

Properties that are expandable will include an x-expandable attribute outlining
the types of resources that may be received in the response.

For example:

``` yaml
definitions:
  ...
  member:
    ...
    x-expandable:
      $ref: '#/components/schemas/member'
```

### `x-resourceId` 

Resources include `x-resourceId` which is a canonical name for each well-known resource.
Not every named resource in the OpenAPI specification has an `x-resourceId` field, but
top level resources with their own operations in the API will each have one.

For example:

``` yaml
# spec.yaml
---
definitions:
  ...
  member:
    ...
    x-resourceId: member
```
