# CORS configuration of buckets

## Sample configuration as an XML file

```
<CORSConfiguration>
    <CORSRule>
        <AllowedOrigin>http://www.example.com</AllowedOrigin>
        <AllowedMethod>PUT</AllowedMethod>
        <AllowedMethod>POST</AllowedMethod>
        <AllowedMethod>DELETE</AllowedMethod>
        <AllowedHeader>*</AllowedHeader>
    </CORSRule>
</CORSConfiguration>
```

This configuration allows you to send cross-domain requests from the `http://www.example.com` website using the PUT, POST, and DELETE methods without any header restrictions.

## Possible elements

| Element | Description |
| ----- | ----- |
| `CORSConfiguration` | Root element of a CORS configuration. May contain a maximum of 100 `CORSRule`<br/> elements. <br/>Path: `/CORSConfiguration`. |
| `CORSRule` | Rule for filtering incoming requests to the resource. Each rule must contain at least one `AllowedMethod` and `AllowedOrigin` element.<br/><br/>Path: `/CORSConfiguration/CORSRule`. |
| `ID` | Unique rule ID (maximum 255 characters).<br/><br/>Optional. You can use it to search for a rule in a file.<br/><br/>Path: `/CORSConfiguration/CORSRule/ID`. |
| `AllowedMethod` | HTTP method (`PUT`, `GET`, `HEAD`, `POST`, or `DELETE`) that can be used in a cross-domain request. Each method should be specified in a separate element. Specify at least one method.<br/><br/>Path: `/CORSConfiguration/CORSRule/AllowedMethod`. |
| `AllowedOrigin` | Website that allows sending cross-domain requests to a bucket. Specify at least one `AllowedOrigin` element. <br/><br/>It may contain no more than one `*` character. Examples: `http://*.example.com`, `*`.<br/><br/>Path: `/CORSConfiguration/CORSRule/AllowedOrigin`. |
| `AllowedHeader` | Header allowed in a request to an object. If multiple headers are allowed, specify each one in a separate `AllowedHeader` element. You can use a single `*` character in the header name to define a template. For example, `<AllowedHeader>*</AllowedHeader>` means that all headers are allowed.<br/><br/>An [OPTIONS](../s3/api-ref/object/options.md) request contains the `Access-Control-Request-Headers` header. [!KEYREF objstorage-name] maps the headers passed in `Access-Control-Request-Headers` to the `AllowedHeader` set and returns a list of allowed headers in response to the `OPTIONS` request.<br/><br/>Path: `/CORSConfiguration/CORSRule/AllowedHeader`. |
| `MaxAgeSeconds` | Time in seconds during which the results of [OPTIONS](../s3/api-ref/object/options.md) requests to objects are cached by the browser.<br/><br/>Path: `/CORSConfiguration/CORSRule/MaxAgeSeconds`. |
| `ExposeHeader` | Header that can be displayed in a JavaScript app in the browser. If multiple headers are allowed, specify each of them in a separate element.<br/><br/>When sending a request to an object, the JavaScript client can only use the headers specified in `ExposeHeader` elements.<br/><br/>Path: `/CORSConfiguration/CORSRule/ExposeHeader`. |

