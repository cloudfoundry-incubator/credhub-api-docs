# Add Permissions

> CredHub CLI

```shell
[not supported]
```

> cURL

```shell
curl "https://example.com/api/v2/permissions" \
  -X POST \
  -d '
  {
    "path": "/example-directory/*",
    "actor": "uaa-user:106f52e2-5d01-4675-8d7a-c05ff9a2c081"
    "operations": ["read", "write"]
  }' \
  -H "authorization: bearer [token]" \
  -H 'content-type: application/json'
```

```json
{
  "uuid": "example-uuid",
  "path": "/example-directory/*",
  "actor": "uaa-user:106f52e2-5d01-4675-8d7a-c05ff9a2c081",
  "operations": ["read","write"]
}
```

```shell
curl "https://example.com/api/v2/permissions" \
  -X POST \
  -d '
  {
    "path": "/example-directory/example-specific-credential",
    "actor": "uaa-user:106f52e2-5d01-4675-8d7a-c05ff9a2c081",
    "operations": ["read", "write"]
  }' \
  -H "authorization: bearer [token]" \
  -H 'content-type: application/json'
```

```json
{
  "uuid": "other-uuid",
  "path": "/example-directory/example-specific-credential",
  "actor": "uaa-user:106f52e2-5d01-4675-8d7a-c05ff9a2c081",
  "operations": ["read","write"]
}
```

This request adds permissions for a path for an actor. You can add permission for a specific credential on a path, as well as all items under a path by using the `*` syntax. 

### HTTP Request

`POST: https://example.com/api/v2/permissions`

### Request Parameters

Parameter | Default | Required | Type | Description
--------- | --------- | --------- | --------- | -----------
path      | none | yes | string | A path where you would like to add a permission to for an actor
actor | none | yes | string | An actor that receives permission at the specified path
operations | none | yes | array of strings | List of operations given to actor for specified path

<sup>1</sup> Authentication-specific identities [explained here.](https://github.com/cloudfoundry-incubator/credhub/blob/master/docs/authentication-identities.md) <br>
<sup>2</sup> Supported operations: read, write, delete, read_acl, write_acl

