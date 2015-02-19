# Generic API Client for NodeRed

This is a node for [NodeRed](http://nodered.org) a tool for easily wiring together hardware devices, APIs and online services. This node provides a generic client for Web APIs by using [Wordnik's Swagger javascript client](https://www.npmjs.org/package/swagger-client). All that is required for you to automatically be able to invoke a given API is to have at your disposal the corresponding [swagger](http://swagger.wordnik.com) description. Check out [Swagger-Spec](https://github.com/wordnik/swagger-spec) for additional information about the Swagger project, including additional libraries with support for other languages and more.

## What's Swagger?

Taken from Swagger's own documentation:

"The goal of Swagger™ is to define a standard, language-agnostic interface to REST APIs which allows both humans and computers to discover and understand the capabilities of the service without access to source code, documentation, or through network traffic inspection. When properly defined via Swagger, a consumer can understand and interact with the remote service with a minimal amount of implementation logic. Similar to what interfaces have done for lower-level programming, Swagger removes the guesswork in calling the service."

## How to Install

Run the following command in the root directory of your Node-RED install

```
npm install node-red-contrib-swagger
```

## Using the Node

Once installed you may be able to invoke any Web API described with Swagger straight away. The only thing that
you need is to create a swagger configuration by adding the URL of some existing swagger documentation. For instance
you can give a go to [Dweet.io](https://dweet.io)'s API by using the following URL `https://dweet.io/play/definition`.

Until we provide advanced search support (work in progress) for existing swagger descriptions online, we
already provide means for serving locally swagger descriptions. This can be used for using your own manually
crafted descriptions or for reusing descriptions made by others.

We have a Github project where we already provide some of descriptions ready to be grabbed and reused.
See [https://github.com/kmi/swagger-descriptions](https://github.com/kmi/swagger-descriptions)

Should you have your own swagger description ready to be used you just need make it available to NodeRed via
an HTTP Server with CORS support. The easiest route is to use the [swagger-descriptions project](https://github.com/kmi/swagger-descriptions)
approach.



## Status

The node is maturing although some issues exist and a couple of features are in the to-do list. 

### Features
Currently the node provides support for:
 - Parsing and invoking Swagger 1.0+ description
 - Content negotiation both for Request and Response content types
 - Authentication via Basic HTTP Auth and API Key 
 - Invocation of APIs (except those with other non-supported authentication mechanisms). 
 
### Issues
Currently the node presents one issue due to an underlying library being used. 
- The parsing of Authentication details does not seem to be done correctly by the swagger-library and therefore authentication details specified at a resource level will not be adequately detected. We expect a solution will soon be implemented at the level of the [Swagger javascript client](https://github.com/wordnik/swagger-js) which would resolve the problem altogether.

### Future Features
We shall be providing the following functionality soon:
- More detailed dynamic documentation of the API being used by the node so as to better help users in figuring out what the request message should look like.
- Support for OAuth 2.0 authentication.

License
-------

Copyright 2014 Knowledge Media Institute - The Open University.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at
[apache.org/licenses/LICENSE-2.0](http://www.apache.org/licenses/LICENSE-2.0)

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.