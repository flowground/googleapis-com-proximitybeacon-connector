# ![LOGO](logo.png) Proximity Beacon **flow**ground Connector

## Description

A generated **flow**ground connector for the Proximity Beacon API (version v1beta1).

Generated from: https://api.apis.guru/v2/specs/googleapis.com/proximitybeacon/v1beta1/swagger.json<br/>
Generated at: 2019-05-23T12:13:34+03:00

## API Description

Registers, manages, indexes, and searches beacons.

## Authorization

Supported authorization schemes:
- OAuth2

For OAuth 2.0 you need to specify OAuth Client credentials as environment variables in the connector repository:
* `OAUTH_CLIENT_ID` - your OAuth client id
* `OAUTH_CLIENT_SECRET` - your OAuth client secret

## Actions

### Given one or more beacon observations, returns any beacon information<br/>
> and attachments accessible to your application. Authorize by using the<br/>
> [API key](https://developers.google.com/beacons/proximity/get-started#request_a_browser_api_key)<br/>
> for the application.

*Tags:* `beaconinfo`

#### Input Parameters
* `$.xgafv` - _optional_ - V1 error format.
    Possible values: 1, 2.
* `access_token` - _optional_ - OAuth access token.
* `alt` - _optional_ - Data format for response.
    Possible values: json, media, proto.
* `callback` - _optional_ - JSONP
* `fields` - _optional_ - Selector specifying which fields to include in a partial response.
* `key` - _optional_ - API key. Your API key identifies your project and provides you with API access, quota, and reports. Required unless you provide an OAuth 2.0 token.
* `oauth_token` - _optional_ - OAuth 2.0 token for the current user.
* `prettyPrint` - _optional_ - Returns response with indentations and line breaks.
* `quotaUser` - _optional_ - Available to use for quota purposes for server-side applications. Can be any arbitrary string assigned to a user, but should not exceed 40 characters.
* `uploadType` - _optional_ - Legacy upload protocol for media (e.g. "media", "multipart").
* `upload_protocol` - _optional_ - Upload protocol for media (e.g. "raw", "multipart").

### Searches the beacon registry for beacons that match the given search<br/>
> criteria. Only those beacons that the client has permission to list<br/>
> will be returned.<br/>
> <br/>
> Authenticate using an [OAuth access token](https://developers.google.com/identity/protocols/OAuth2)<br/>
> from a signed-in user with **viewer**, **Is owner** or **Can edit**<br/>
> permissions in the Google Developers Console project.

*Tags:* `beacons`

#### Input Parameters
* `pageSize` - _optional_ - The maximum number of records to return for this request, up to a
server-defined upper limit.
* `pageToken` - _optional_ - A pagination token obtained from a previous request to list beacons.
* `projectId` - _optional_ - The project id to list beacons under. If not present then the project
credential that made the request is used as the project.
Optional.
* `q` - _optional_ - Filter query string that supports the following field filters:

* **description:`"<string>"`**
  For example: **description:"Room 3"**
  Returns beacons whose description matches tokens in the string "Room 3"
  (not necessarily that exact string).
  The string must be double-quoted.
* **status:`<enum>`**
  For example: **status:active**
  Returns beacons whose status matches the given value. Values must be
  one of the Beacon.Status enum values (case insensitive). Accepts
  multiple filters which will be combined with OR logic.
* **stability:`<enum>`**
  For example: **stability:mobile**
  Returns beacons whose expected stability matches the given value.
  Values must be one of the Beacon.Stability enum values (case
  insensitive). Accepts multiple filters which will be combined with
  OR logic.
* **place\_id:`"<string>"`**
  For example: **place\_id:"ChIJVSZzVR8FdkgRXGmmm6SslKw="**
  Returns beacons explicitly registered at the given place, expressed as
  a Place ID obtained from [Google Places API](/places/place-id). Does not
  match places inside the given place. Does not consider the beacon's
  actual location (which may be different from its registered place).
  Accepts multiple filters that will be combined with OR logic. The place
  ID must be double-quoted.
* **registration\_time`[<|>|<=|>=]<integer>`**
  For example: **registration\_time>=1433116800**
  Returns beacons whose registration time matches the given filter.
  Supports the operators: <, >, <=, and >=. Timestamp must be expressed as
  an integer number of seconds since midnight January 1, 1970 UTC. Accepts
  at most two filters that will be combined with AND logic, to support
  "between" semantics. If more than two are supplied, the latter ones are
  ignored.
* **lat:`<double> lng:<double> radius:<integer>`**
  For example: **lat:51.1232343 lng:-1.093852 radius:1000**
  Returns beacons whose registered location is within the given circle.
  When any of these fields are given, all are required. Latitude and
  longitude must be decimal degrees between -90.0 and 90.0 and between
  -180.0 and 180.0 respectively. Radius must be an integer number of
  meters between 10 and 1,000,000 (1000 km).
* **property:`"<string>=<string>"`**
  For example: **property:"battery-type=CR2032"**
  Returns beacons which have a property of the given name and value.
  Supports multiple filters which will be combined with OR logic.
  The entire name=value string must be double-quoted as one string.
* **attachment\_type:`"<string>"`**
  For example: **attachment_type:"my-namespace/my-type"**
  Returns beacons having at least one attachment of the given namespaced
  type. Supports "any within this namespace" via the partial wildcard
  syntax: "my-namespace/*". Supports multiple filters which will be
  combined with OR logic. The string must be double-quoted.
* **indoor\_level:`"<string>"`**
  For example: **indoor\_level:"1"**
  Returns beacons which are located on the given indoor level. Accepts
  multiple filters that will be combined with OR logic.

Multiple filters on the same field are combined with OR logic (except
registration_time which is combined with AND logic).
Multiple filters on different fields are combined with AND logic.
Filters should be separated by spaces.

As with any HTTP query string parameter, the whole filter expression must
be URL-encoded.

Example REST request:
`GET /v1beta1/beacons?q=status:active%20lat:51.123%20lng:-1.095%20radius:1000`
* `fields` - _optional_ - Selector specifying which fields to include in a partial response.
* `key` - _optional_ - API key. Your API key identifies your project and provides you with API access, quota, and reports. Required unless you provide an OAuth 2.0 token.
* `oauth_token` - _optional_ - OAuth 2.0 token for the current user.
* `prettyPrint` - _optional_ - Returns response with indentations and line breaks.
* `quotaUser` - _optional_ - Available to use for quota purposes for server-side applications. Can be any arbitrary string assigned to a user, but should not exceed 40 characters.
* `uploadType` - _optional_ - Legacy upload protocol for media (e.g. "media", "multipart").
* `upload_protocol` - _optional_ - Upload protocol for media (e.g. "raw", "multipart").

### Registers a previously unregistered beacon given its `advertisedId`.<br/>
> These IDs are unique within the system. An ID can be registered only once.<br/>
> <br/>
> Authenticate using an [OAuth access token](https://developers.google.com/identity/protocols/OAuth2)<br/>
> from a signed-in user with **Is owner** or **Can edit** permissions in the<br/>
> Google Developers Console project.

*Tags:* `beacons`

#### Input Parameters
* `projectId` - _optional_ - The project id of the project the beacon will be registered to. If
the project id is not specified then the project making the request
is used.
Optional.
* `access_token` - _optional_ - OAuth access token.
* `alt` - _optional_ - Data format for response.
    Possible values: json, media, proto.
* `callback` - _optional_ - JSONP
* `fields` - _optional_ - Selector specifying which fields to include in a partial response.
* `key` - _optional_ - API key. Your API key identifies your project and provides you with API access, quota, and reports. Required unless you provide an OAuth 2.0 token.
* `oauth_token` - _optional_ - OAuth 2.0 token for the current user.
* `prettyPrint` - _optional_ - Returns response with indentations and line breaks.
* `quotaUser` - _optional_ - Available to use for quota purposes for server-side applications. Can be any arbitrary string assigned to a user, but should not exceed 40 characters.
* `uploadType` - _optional_ - Legacy upload protocol for media (e.g. "media", "multipart").
* `upload_protocol` - _optional_ - Upload protocol for media (e.g. "raw", "multipart").

### Gets the Proximity Beacon API's current public key and associated<br/>
> parameters used to initiate the Diffie-Hellman key exchange required to<br/>
> register a beacon that broadcasts the Eddystone-EID format. This key<br/>
> changes periodically; clients may cache it and re-use the same public key<br/>
> to provision and register multiple beacons. However, clients should be<br/>
> prepared to refresh this key when they encounter an error registering an<br/>
> Eddystone-EID beacon.

*Tags:* `v1beta1`

#### Input Parameters
* `$.xgafv` - _optional_ - V1 error format.
    Possible values: 1, 2.
* `access_token` - _optional_ - OAuth access token.
* `alt` - _optional_ - Data format for response.
    Possible values: json, media, proto.
* `callback` - _optional_ - JSONP
* `fields` - _optional_ - Selector specifying which fields to include in a partial response.
* `key` - _optional_ - API key. Your API key identifies your project and provides you with API access, quota, and reports. Required unless you provide an OAuth 2.0 token.
* `oauth_token` - _optional_ - OAuth 2.0 token for the current user.
* `prettyPrint` - _optional_ - Returns response with indentations and line breaks.
* `quotaUser` - _optional_ - Available to use for quota purposes for server-side applications. Can be any arbitrary string assigned to a user, but should not exceed 40 characters.
* `uploadType` - _optional_ - Legacy upload protocol for media (e.g. "media", "multipart").
* `upload_protocol` - _optional_ - Upload protocol for media (e.g. "raw", "multipart").

### Lists all attachment namespaces owned by your Google Developers Console<br/>
> project. Attachment data associated with a beacon must include a<br/>
> namespaced type, and the namespace must be owned by your project.<br/>
> <br/>
> Authenticate using an [OAuth access token](https://developers.google.com/identity/protocols/OAuth2)<br/>
> from a signed-in user with **viewer**, **Is owner** or **Can edit**<br/>
> permissions in the Google Developers Console project.

*Tags:* `namespaces`

#### Input Parameters
* `projectId` - _optional_ - The project id to list namespaces under.
Optional.
* `access_token` - _optional_ - OAuth access token.
* `alt` - _optional_ - Data format for response.
    Possible values: json, media, proto.
* `callback` - _optional_ - JSONP
* `fields` - _optional_ - Selector specifying which fields to include in a partial response.
* `key` - _optional_ - API key. Your API key identifies your project and provides you with API access, quota, and reports. Required unless you provide an OAuth 2.0 token.
* `oauth_token` - _optional_ - OAuth 2.0 token for the current user.
* `prettyPrint` - _optional_ - Returns response with indentations and line breaks.
* `quotaUser` - _optional_ - Available to use for quota purposes for server-side applications. Can be any arbitrary string assigned to a user, but should not exceed 40 characters.
* `uploadType` - _optional_ - Legacy upload protocol for media (e.g. "media", "multipart").
* `upload_protocol` - _optional_ - Upload protocol for media (e.g. "raw", "multipart").

### Deletes the specified attachment for the given beacon. Each attachment has<br/>
> a unique attachment name (`attachmentName`) which is returned when you<br/>
> fetch the attachment data via this API. You specify this with the delete<br/>
> request to control which attachment is removed. This operation cannot be<br/>
> undone.<br/>
> <br/>
> Authenticate using an [OAuth access token](https://developers.google.com/identity/protocols/OAuth2)<br/>
> from a signed-in user with **Is owner** or **Can edit** permissions in the<br/>
> Google Developers Console project.

*Tags:* `beacons`

#### Input Parameters
* `attachmentName` - _required_ - The attachment name (`attachmentName`) of
the attachment to remove. For example:
`beacons/3!893737abc9/attachments/c5e937-af0-494-959-ec49d12738`. For
Eddystone-EID beacons, the beacon ID portion (`3!893737abc9`) may be the
beacon's current EID, or its "stable" Eddystone-UID.
Required.
* `projectId` - _optional_ - The project id of the attachment to delete. If not provided, the project
that is making the request is used.
Optional.
* `alt` - _optional_ - Data format for response.
    Possible values: json, media, proto.
* `callback` - _optional_ - JSONP
* `fields` - _optional_ - Selector specifying which fields to include in a partial response.
* `key` - _optional_ - API key. Your API key identifies your project and provides you with API access, quota, and reports. Required unless you provide an OAuth 2.0 token.
* `oauth_token` - _optional_ - OAuth 2.0 token for the current user.
* `prettyPrint` - _optional_ - Returns response with indentations and line breaks.
* `quotaUser` - _optional_ - Available to use for quota purposes for server-side applications. Can be any arbitrary string assigned to a user, but should not exceed 40 characters.
* `uploadType` - _optional_ - Legacy upload protocol for media (e.g. "media", "multipart").
* `upload_protocol` - _optional_ - Upload protocol for media (e.g. "raw", "multipart").

### Deletes the specified beacon including all diagnostics data for the beacon<br/>
> as well as any attachments on the beacon (including those belonging to<br/>
> other projects). This operation cannot be undone.<br/>
> <br/>
> Authenticate using an [OAuth access token](https://developers.google.com/identity/protocols/OAuth2)<br/>
> from a signed-in user with **Is owner** or **Can edit** permissions in the<br/>
> Google Developers Console project.

*Tags:* `beacons`

#### Input Parameters
* `beaconName` - _required_ - Beacon that should be deleted. A beacon name has the format
"beacons/N!beaconId" where the beaconId is the base16 ID broadcast by
the beacon and N is a code for the beacon's type. Possible values are
`3` for Eddystone-UID, `4` for Eddystone-EID, `1` for iBeacon, or `5`
for AltBeacon. For Eddystone-EID beacons, you may use either the
current EID or the beacon's "stable" UID.
Required.
* `projectId` - _optional_ - The project id of the beacon to delete. If not provided, the project
that is making the request is used.
Optional.
* `alt` - _optional_ - Data format for response.
    Possible values: json, media, proto.
* `callback` - _optional_ - JSONP
* `fields` - _optional_ - Selector specifying which fields to include in a partial response.
* `key` - _optional_ - API key. Your API key identifies your project and provides you with API access, quota, and reports. Required unless you provide an OAuth 2.0 token.
* `oauth_token` - _optional_ - OAuth 2.0 token for the current user.
* `prettyPrint` - _optional_ - Returns response with indentations and line breaks.
* `quotaUser` - _optional_ - Available to use for quota purposes for server-side applications. Can be any arbitrary string assigned to a user, but should not exceed 40 characters.
* `uploadType` - _optional_ - Legacy upload protocol for media (e.g. "media", "multipart").
* `upload_protocol` - _optional_ - Upload protocol for media (e.g. "raw", "multipart").

### Returns detailed information about the specified beacon.<br/>
> <br/>
> Authenticate using an [OAuth access token](https://developers.google.com/identity/protocols/OAuth2)<br/>
> from a signed-in user with **viewer**, **Is owner** or **Can edit**<br/>
> permissions in the Google Developers Console project.<br/>
> <br/>
> Requests may supply an Eddystone-EID beacon name in the form:<br/>
> `beacons/4!beaconId` where the `beaconId` is the base16 ephemeral ID<br/>
> broadcast by the beacon. The returned `Beacon` object will contain the<br/>
> beacon's stable Eddystone-UID. Clients not authorized to resolve the<br/>
> beacon's ephemeral Eddystone-EID broadcast will receive an error.

*Tags:* `beacons`

#### Input Parameters
* `beaconName` - _required_ - Resource name of this beacon. A beacon name has the format
"beacons/N!beaconId" where the beaconId is the base16 ID broadcast by
the beacon and N is a code for the beacon's type. Possible values are
`3` for Eddystone-UID, `4` for Eddystone-EID, `1` for iBeacon, or `5`
for AltBeacon. For Eddystone-EID beacons, you may use either the
current EID or the beacon's "stable" UID.
Required.
* `projectId` - _optional_ - The project id of the beacon to request. If the project id is not specified
then the project making the request is used. The project id must match the
project that owns the beacon.
Optional.
* `alt` - _optional_ - Data format for response.
    Possible values: json, media, proto.
* `callback` - _optional_ - JSONP
* `fields` - _optional_ - Selector specifying which fields to include in a partial response.
* `key` - _optional_ - API key. Your API key identifies your project and provides you with API access, quota, and reports. Required unless you provide an OAuth 2.0 token.
* `oauth_token` - _optional_ - OAuth 2.0 token for the current user.
* `prettyPrint` - _optional_ - Returns response with indentations and line breaks.
* `quotaUser` - _optional_ - Available to use for quota purposes for server-side applications. Can be any arbitrary string assigned to a user, but should not exceed 40 characters.
* `uploadType` - _optional_ - Legacy upload protocol for media (e.g. "media", "multipart").
* `upload_protocol` - _optional_ - Upload protocol for media (e.g. "raw", "multipart").

### Updates the information about the specified beacon. **Any field that you do<br/>
> not populate in the submitted beacon will be permanently erased**, so you<br/>
> should follow the "read, modify, write" pattern to avoid inadvertently<br/>
> destroying data.<br/>
> <br/>
> Changes to the beacon status via this method will be  silently ignored.<br/>
> To update beacon status, use the separate methods on this API for<br/>
> activation, deactivation, and decommissioning.<br/>
> Authenticate using an [OAuth access token](https://developers.google.com/identity/protocols/OAuth2)<br/>
> from a signed-in user with **Is owner** or **Can edit** permissions in the<br/>
> Google Developers Console project.

*Tags:* `beacons`

#### Input Parameters
* `beaconName` - _required_ - Resource name of this beacon. A beacon name has the format
"beacons/N!beaconId" where the beaconId is the base16 ID broadcast by
the beacon and N is a code for the beacon's type. Possible values are
`3` for Eddystone, `1` for iBeacon, or `5` for AltBeacon.

This field must be left empty when registering. After reading a beacon,
clients can use the name for future operations.
* `projectId` - _optional_ - The project id of the beacon to update. If the project id is not
specified then the project making the request is used. The project id
must match the project that owns the beacon.
Optional.
* `alt` - _optional_ - Data format for response.
    Possible values: json, media, proto.
* `callback` - _optional_ - JSONP
* `fields` - _optional_ - Selector specifying which fields to include in a partial response.
* `key` - _optional_ - API key. Your API key identifies your project and provides you with API access, quota, and reports. Required unless you provide an OAuth 2.0 token.
* `oauth_token` - _optional_ - OAuth 2.0 token for the current user.
* `prettyPrint` - _optional_ - Returns response with indentations and line breaks.
* `quotaUser` - _optional_ - Available to use for quota purposes for server-side applications. Can be any arbitrary string assigned to a user, but should not exceed 40 characters.
* `uploadType` - _optional_ - Legacy upload protocol for media (e.g. "media", "multipart").
* `upload_protocol` - _optional_ - Upload protocol for media (e.g. "raw", "multipart").

### Returns the attachments for the specified beacon that match the specified<br/>
> namespaced-type pattern.<br/>
> <br/>
> To control which namespaced types are returned, you add the<br/>
> `namespacedType` query parameter to the request. You must either use<br/>
> `*/*`, to return all attachments, or the namespace must be one of<br/>
> the ones returned from the  `namespaces` endpoint.<br/>
> <br/>
> Authenticate using an [OAuth access token](https://developers.google.com/identity/protocols/OAuth2)<br/>
> from a signed-in user with **viewer**, **Is owner** or **Can edit**<br/>
> permissions in the Google Developers Console project.

*Tags:* `beacons`

#### Input Parameters
* `beaconName` - _required_ - Beacon whose attachments should be fetched. A beacon name has the
format "beacons/N!beaconId" where the beaconId is the base16 ID broadcast
by the beacon and N is a code for the beacon's type. Possible values are
`3` for Eddystone-UID, `4` for Eddystone-EID, `1` for iBeacon, or `5`
for AltBeacon. For Eddystone-EID beacons, you may use either the
current EID or the beacon's "stable" UID.
Required.
* `namespacedType` - _optional_ - Specifies the namespace and type of attachment to include in response in
<var>namespace/type</var> format. Accepts `*/*` to specify
"all types in all namespaces".
* `projectId` - _optional_ - The project id to list beacon attachments under. This field can be
used when "*" is specified to mean all attachment namespaces. Projects
may have multiple attachments with multiple namespaces. If "*" is
specified and the projectId string is empty, then the project
making the request is used.
Optional.
* `callback` - _optional_ - JSONP
* `fields` - _optional_ - Selector specifying which fields to include in a partial response.
* `key` - _optional_ - API key. Your API key identifies your project and provides you with API access, quota, and reports. Required unless you provide an OAuth 2.0 token.
* `oauth_token` - _optional_ - OAuth 2.0 token for the current user.
* `prettyPrint` - _optional_ - Returns response with indentations and line breaks.
* `quotaUser` - _optional_ - Available to use for quota purposes for server-side applications. Can be any arbitrary string assigned to a user, but should not exceed 40 characters.
* `uploadType` - _optional_ - Legacy upload protocol for media (e.g. "media", "multipart").
* `upload_protocol` - _optional_ - Upload protocol for media (e.g. "raw", "multipart").

### Associates the given data with the specified beacon. Attachment data must<br/>
> contain two parts:<br/>
> <ul><br/>
> <li>A namespaced type.</li><br/>
> <li>The actual attachment data itself.</li><br/>
> </ul><br/>
> The namespaced type consists of two parts, the namespace and the type.<br/>
> The namespace must be one of the values returned by the `namespaces`<br/>
> endpoint, while the type can be a string of any characters except for the<br/>
> forward slash (`/`) up to 100 characters in length.<br/>
> <br/>
> Attachment data can be up to 1024 bytes long.<br/>
> <br/>
> Authenticate using an [OAuth access token](https://developers.google.com/identity/protocols/OAuth2)<br/>
> from a signed-in user with **Is owner** or **Can edit** permissions in the<br/>
> Google Developers Console project.

*Tags:* `beacons`

#### Input Parameters
* `beaconName` - _required_ - Beacon on which the attachment should be created. A beacon name has the
format "beacons/N!beaconId" where the beaconId is the base16 ID broadcast
by the beacon and N is a code for the beacon's type. Possible values are
`3` for Eddystone-UID, `4` for Eddystone-EID, `1` for iBeacon, or `5`
for AltBeacon. For Eddystone-EID beacons, you may use either the
current EID or the beacon's "stable" UID.
Required.
* `projectId` - _optional_ - The project id of the project the attachment will belong to. If
the project id is not specified then the project making the request
is used.
Optional.
* `alt` - _optional_ - Data format for response.
    Possible values: json, media, proto.
* `callback` - _optional_ - JSONP
* `fields` - _optional_ - Selector specifying which fields to include in a partial response.
* `key` - _optional_ - API key. Your API key identifies your project and provides you with API access, quota, and reports. Required unless you provide an OAuth 2.0 token.
* `oauth_token` - _optional_ - OAuth 2.0 token for the current user.
* `prettyPrint` - _optional_ - Returns response with indentations and line breaks.
* `quotaUser` - _optional_ - Available to use for quota purposes for server-side applications. Can be any arbitrary string assigned to a user, but should not exceed 40 characters.
* `uploadType` - _optional_ - Legacy upload protocol for media (e.g. "media", "multipart").
* `upload_protocol` - _optional_ - Upload protocol for media (e.g. "raw", "multipart").

### Deletes multiple attachments on a given beacon. This operation is<br/>
> permanent and cannot be undone.<br/>
> <br/>
> You can optionally specify `namespacedType` to choose which attachments<br/>
> should be deleted. If you do not specify `namespacedType`,  all your<br/>
> attachments on the given beacon will be deleted. You also may explicitly<br/>
> specify `*/*` to delete all.<br/>
> <br/>
> Authenticate using an [OAuth access token](https://developers.google.com/identity/protocols/OAuth2)<br/>
> from a signed-in user with **Is owner** or **Can edit** permissions in the<br/>
> Google Developers Console project.

*Tags:* `beacons`

#### Input Parameters
* `beaconName` - _required_ - The beacon whose attachments should be deleted. A beacon name has the
format "beacons/N!beaconId" where the beaconId is the base16 ID broadcast
by the beacon and N is a code for the beacon's type. Possible values are
`3` for Eddystone-UID, `4` for Eddystone-EID, `1` for iBeacon, or `5`
for AltBeacon. For Eddystone-EID beacons, you may use either the
current EID or the beacon's "stable" UID.
Required.
* `namespacedType` - _optional_ - Specifies the namespace and type of attachments to delete in
`namespace/type` format. Accepts `*/*` to specify
"all types in all namespaces".
Optional.
* `projectId` - _optional_ - The project id to delete beacon attachments under. This field can be
used when "*" is specified to mean all attachment namespaces. Projects
may have multiple attachments with multiple namespaces. If "*" is
specified and the projectId string is empty, then the project
making the request is used.
Optional.
* `callback` - _optional_ - JSONP
* `fields` - _optional_ - Selector specifying which fields to include in a partial response.
* `key` - _optional_ - API key. Your API key identifies your project and provides you with API access, quota, and reports. Required unless you provide an OAuth 2.0 token.
* `oauth_token` - _optional_ - OAuth 2.0 token for the current user.
* `prettyPrint` - _optional_ - Returns response with indentations and line breaks.
* `quotaUser` - _optional_ - Available to use for quota purposes for server-side applications. Can be any arbitrary string assigned to a user, but should not exceed 40 characters.
* `uploadType` - _optional_ - Legacy upload protocol for media (e.g. "media", "multipart").
* `upload_protocol` - _optional_ - Upload protocol for media (e.g. "raw", "multipart").

### List the diagnostics for a single beacon. You can also list diagnostics for<br/>
> all the beacons owned by your Google Developers Console project by using<br/>
> the beacon name `beacons/-`.<br/>
> <br/>
> Authenticate using an [OAuth access token](https://developers.google.com/identity/protocols/OAuth2)<br/>
> from a signed-in user with **viewer**, **Is owner** or **Can edit**<br/>
> permissions in the Google Developers Console project.

*Tags:* `beacons`

#### Input Parameters
* `alertFilter` - _optional_ - Requests only beacons that have the given alert. For example, to find
beacons that have low batteries use `alert_filter=LOW_BATTERY`.
    Possible values: ALERT_UNSPECIFIED, WRONG_LOCATION, LOW_BATTERY, LOW_ACTIVITY.
* `beaconName` - _required_ - Beacon that the diagnostics are for.
* `pageSize` - _optional_ - Specifies the maximum number of results to return. Defaults to
10. Maximum 1000. Optional.
* `pageToken` - _optional_ - Requests results that occur after the `page_token`, obtained from the
response to a previous request. Optional.
* `projectId` - _optional_ - Requests only diagnostic records for the given project id. If not set,
then the project making the request will be used for looking up
diagnostic records. Optional.
* `key` - _optional_ - API key. Your API key identifies your project and provides you with API access, quota, and reports. Required unless you provide an OAuth 2.0 token.
* `oauth_token` - _optional_ - OAuth 2.0 token for the current user.
* `prettyPrint` - _optional_ - Returns response with indentations and line breaks.
* `quotaUser` - _optional_ - Available to use for quota purposes for server-side applications. Can be any arbitrary string assigned to a user, but should not exceed 40 characters.
* `uploadType` - _optional_ - Legacy upload protocol for media (e.g. "media", "multipart").
* `upload_protocol` - _optional_ - Upload protocol for media (e.g. "raw", "multipart").

### Activates a beacon. A beacon that is active will return information<br/>
> and attachment data when queried via `beaconinfo.getforobserved`.<br/>
> Calling this method on an already active beacon will do nothing (but<br/>
> will return a successful response code).<br/>
> <br/>
> Authenticate using an [OAuth access token](https://developers.google.com/identity/protocols/OAuth2)<br/>
> from a signed-in user with **Is owner** or **Can edit** permissions in the<br/>
> Google Developers Console project.

*Tags:* `beacons`

#### Input Parameters
* `beaconName` - _required_ - Beacon that should be activated. A beacon name has the format
"beacons/N!beaconId" where the beaconId is the base16 ID broadcast by
the beacon and N is a code for the beacon's type. Possible values are
`3` for Eddystone-UID, `4` for Eddystone-EID, `1` for iBeacon, or `5`
for AltBeacon. For Eddystone-EID beacons, you may use either the
current EID or the beacon's "stable" UID.
Required.
* `projectId` - _optional_ - The project id of the beacon to activate. If the project id is not
specified then the project making the request is used. The project id
must match the project that owns the beacon.
Optional.
* `alt` - _optional_ - Data format for response.
    Possible values: json, media, proto.
* `callback` - _optional_ - JSONP
* `fields` - _optional_ - Selector specifying which fields to include in a partial response.
* `key` - _optional_ - API key. Your API key identifies your project and provides you with API access, quota, and reports. Required unless you provide an OAuth 2.0 token.
* `oauth_token` - _optional_ - OAuth 2.0 token for the current user.
* `prettyPrint` - _optional_ - Returns response with indentations and line breaks.
* `quotaUser` - _optional_ - Available to use for quota purposes for server-side applications. Can be any arbitrary string assigned to a user, but should not exceed 40 characters.
* `uploadType` - _optional_ - Legacy upload protocol for media (e.g. "media", "multipart").
* `upload_protocol` - _optional_ - Upload protocol for media (e.g. "raw", "multipart").

### Deactivates a beacon. Once deactivated, the API will not return<br/>
> information nor attachment data for the beacon when queried via<br/>
> `beaconinfo.getforobserved`. Calling this method on an already inactive<br/>
> beacon will do nothing (but will return a successful response code).<br/>
> <br/>
> Authenticate using an [OAuth access token](https://developers.google.com/identity/protocols/OAuth2)<br/>
> from a signed-in user with **Is owner** or **Can edit** permissions in the<br/>
> Google Developers Console project.

*Tags:* `beacons`

#### Input Parameters
* `beaconName` - _required_ - Beacon that should be deactivated. A beacon name has the format
"beacons/N!beaconId" where the beaconId is the base16 ID broadcast by
the beacon and N is a code for the beacon's type. Possible values are
`3` for Eddystone-UID, `4` for Eddystone-EID, `1` for iBeacon, or `5`
for AltBeacon. For Eddystone-EID beacons, you may use either the
current EID or the beacon's "stable" UID.
Required.
* `projectId` - _optional_ - The project id of the beacon to deactivate. If the project id is not
specified then the project making the request is used. The project id must
match the project that owns the beacon.
Optional.
* `alt` - _optional_ - Data format for response.
    Possible values: json, media, proto.
* `callback` - _optional_ - JSONP
* `fields` - _optional_ - Selector specifying which fields to include in a partial response.
* `key` - _optional_ - API key. Your API key identifies your project and provides you with API access, quota, and reports. Required unless you provide an OAuth 2.0 token.
* `oauth_token` - _optional_ - OAuth 2.0 token for the current user.
* `prettyPrint` - _optional_ - Returns response with indentations and line breaks.
* `quotaUser` - _optional_ - Available to use for quota purposes for server-side applications. Can be any arbitrary string assigned to a user, but should not exceed 40 characters.
* `uploadType` - _optional_ - Legacy upload protocol for media (e.g. "media", "multipart").
* `upload_protocol` - _optional_ - Upload protocol for media (e.g. "raw", "multipart").

### Decommissions the specified beacon in the service. This beacon will no<br/>
> longer be returned from `beaconinfo.getforobserved`. This operation is<br/>
> permanent -- you will not be able to re-register a beacon with this ID<br/>
> again.<br/>
> <br/>
> Authenticate using an [OAuth access token](https://developers.google.com/identity/protocols/OAuth2)<br/>
> from a signed-in user with **Is owner** or **Can edit** permissions in the<br/>
> Google Developers Console project.

*Tags:* `beacons`

#### Input Parameters
* `beaconName` - _required_ - Beacon that should be decommissioned. A beacon name has the format
"beacons/N!beaconId" where the beaconId is the base16 ID broadcast by
the beacon and N is a code for the beacon's type. Possible values are
`3` for Eddystone-UID, `4` for Eddystone-EID, `1` for iBeacon, or `5`
for AltBeacon. For Eddystone-EID beacons, you may use either the
current EID of the beacon's "stable" UID.
Required.
* `projectId` - _optional_ - The project id of the beacon to decommission. If the project id is not
specified then the project making the request is used. The project id
must match the project that owns the beacon.
Optional.
* `alt` - _optional_ - Data format for response.
    Possible values: json, media, proto.
* `callback` - _optional_ - JSONP
* `fields` - _optional_ - Selector specifying which fields to include in a partial response.
* `key` - _optional_ - API key. Your API key identifies your project and provides you with API access, quota, and reports. Required unless you provide an OAuth 2.0 token.
* `oauth_token` - _optional_ - OAuth 2.0 token for the current user.
* `prettyPrint` - _optional_ - Returns response with indentations and line breaks.
* `quotaUser` - _optional_ - Available to use for quota purposes for server-side applications. Can be any arbitrary string assigned to a user, but should not exceed 40 characters.
* `uploadType` - _optional_ - Legacy upload protocol for media (e.g. "media", "multipart").
* `upload_protocol` - _optional_ - Upload protocol for media (e.g. "raw", "multipart").

### Updates the information about the specified namespace. Only the namespace<br/>
> visibility can be updated.

*Tags:* `namespaces`

#### Input Parameters
* `namespaceName` - _required_ - Resource name of this namespace. Namespaces names have the format:
<code>namespaces/<var>namespace</var></code>.
* `projectId` - _optional_ - The project id of the namespace to update. If the project id is not
specified then the project making the request is used. The project id
must match the project that owns the beacon.
Optional.
* `alt` - _optional_ - Data format for response.
    Possible values: json, media, proto.
* `callback` - _optional_ - JSONP
* `fields` - _optional_ - Selector specifying which fields to include in a partial response.
* `key` - _optional_ - API key. Your API key identifies your project and provides you with API access, quota, and reports. Required unless you provide an OAuth 2.0 token.
* `oauth_token` - _optional_ - OAuth 2.0 token for the current user.
* `prettyPrint` - _optional_ - Returns response with indentations and line breaks.
* `quotaUser` - _optional_ - Available to use for quota purposes for server-side applications. Can be any arbitrary string assigned to a user, but should not exceed 40 characters.
* `uploadType` - _optional_ - Legacy upload protocol for media (e.g. "media", "multipart").
* `upload_protocol` - _optional_ - Upload protocol for media (e.g. "raw", "multipart").

## License

**flow**ground :- Telekom iPaaS / googleapis-com-proximitybeacon-connector<br/>
Copyright © 2019, [Deutsche Telekom AG](https://www.telekom.de)<br/>
contact: flowground@telekom.de

All files of this connector are licensed under the Apache 2.0 License. For details
see the file LICENSE on the toplevel directory.
