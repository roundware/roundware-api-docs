# Common Scenarios

The following are common sequences of API calls that are useful both for testing as well as for implementation. Most core Roundware functionality requires a series of API calls to accomplish the desired result.

## Initialize Client

Roundware clients will need to make a series of requests to the server to initialize and configure the UI.

### 1. Get token

Making a request to the `users/` endpoint with unique `device_id` returns a token to be used with all subsequent requests.

``POST localhost:8888/api/2/users/``

### 2. Establish Session

Each time a Roundware client is instantiated, it needs to create a new Session:

``POST localhost:8888/api/2/sessions/``

### 3. Get Project Info

Various config data is stored on the server to maximize flexibility and is used to initialize Roundware client UIs as well as control certain functionality. Currently, clients are all single-project and therefore have their `project_id` hard-coded, but in the future, clients will be able to choose from available projects and will subsequently send the selected `project_id` to the server in this request.

``GET localhost:8888/api/2/projects/:id/?session_id=1``

### 4. Get Tag Info

Tags are also stored on the server and are retrieved for use in the UI.

``GET localhost:8888/api/2/projects/:id/tags/?session_id=1``

### 5. Get UI Info

Tags are grouped and ordered within client UIs based on data stored in UI Groups and UI Items

``GET localhost:8888/api/2/projects/:id/uigroups/?session_id=1``

These are the basic initialization steps, though some projects will require variations and/or additions to these.

## Request Stream

### 1. Create Stream

Streams are created on a one-to-one relationship with Sessions. A Stream can be re-created during a Session as needed, but the `stream_id` will remain the unchanged and the same as `session_id`.

``POST localhost:8888/api/2/streams/:id/``

### 2. Move Listener

Every time the Roundware client senses a new position, it sends a `PATCH streams/` request with the updated `latitude` and `longitude` values which cause the server to remix the Speaker audio and filter the available Assets in the playlist.

``PATCH localhost:8888/api/2/streams/:id/``

### 3. Modify Stream

Users can filter their Stream by Tags. This is the same `PATCH streams/` request as for location changes and can in fact be combined by including `tag_ids` `latitude` and `longitude` params in the same request.

``PATCH localhost:8888/api/2/streams/:id/``

## Upload Asset

### 1. Create Envelope

Envelopes are used to bundle Assets together and all Assets, even if not bundled, require an associated Envelope.

``POST localhost:8888/api/2/envelopes/``

### 2. Update Envelope With Asset

An Asset is created locally on the client and then uploaded to the server in a `PATCH envelopes/` request which includes the binary file as well as all associated metadata.

``PATCH localhost:8888/api/2/envelopes/:id/``
