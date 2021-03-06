# Introduction

Overlays pattern is a generic concept for data composition.

The aim of this document is to explore and try to define a generic 
set of rules and attributes which such a pattern could provide.

# Properties

* Discoverability - Allow easy discoverability of the objects within a pattern. This helps for adoption, reusability, user-friendly etc.
* Identification - Allow to verify that we are talking about the same layer
* Versioning - Allow to verify the version of the layer
* Immutability - Allow to ensure that the layer won't change in the future
* Interoperability - Allow to reuse same layer independent from any concrete implementation
* Decentralization - Allow to avoid vendor locking and to not relay on centralize repository

# Background

It seems that the concept of general overlays seems to be very interesting in
different spaces. The concept was born some time ago while we thought about new
modern file format which supposes to be composed out of different layers. Then the
idea was buried for some time and reborn again within Semantic WG in
Hyperledger where we started defining schema and overlays for decentralize
global storage.


# Overlays 
## Why we need it?

We don't know yet. But it is very interesting to evaluate possibility if
something like that could solve some problems.

Some potential problems which could be solved by this approach:
* Provide unify data language for decentralize economy including: data exchange, data storage, communication etc. 
* Allow building global decentralize data storage for society benefits
* Provide an overall framework for dealing with data including consent, privacy, traceability etc.

We already started implementing this approach within the schema and overlays concept in Semantic WG. 
The idea behind `Overlays` is to create unify notation for data which can be used in multiple cases:

* Data Vault - as a normalization solution, share and store data.
* Data capture - collecting data from different sources in a standardize and reusable way
* File format - Multi-layer file format which separate content, presentation layer, and potential logic layer
* Verifiable credentials - for example as a reusable schema with different encodings

We don't know yet if all those use cases are valid and/or if we should cover all of them or more. It seems that all of them have a similar nature. Which could be described as follow:

* Static or dynamic base - the place where the base subject is (content of the file, schema base for data, database model, protocol data description (schema) etc..)
* Layers - a different type of layers from static through-composed and ad-hoc layers. They can serve as a coloration, enriching or extending base without the need to change it. 

## Example

### [Schema and Overlays](https://github.com/THCLab/schema-cake) - Data capture 
### File format

* Dynamic base - would be content which we are creating 
* Layers:
  * Subset overlay - could reduce the content within the document base on who is reading it. Show just a brief description or hide technicalities. 
  * Information - annotation/comments or contextual information
  * Language - translations - same document supporting multiple languages at the same time. 
  
### Verifaible credentials

* Static base - simple schema representing all attributes which are subject of VC
* Layers:
  * Information - annotation/comments or contextual information
  * Encoding - crypto material used for encoding (ZKP)
  * ...

### Across use cases 

Actors:
* Jan (Software Engineer)
* Anna (Computer store owner)
* Post (Postal service)
* Krzyś (Research scientist)
* PDC Inc (Package Delivery company

Objects:
user_address - schema base representing user home address 

0) Jan and Post
Jan visits his local post service `Post` where he identifies himself and receive Verifiable Claim which (using `user_address` schema with encoding - a crypto overlay on top)  later on can use for different services.

1) Jan and Anna
Jan wants to buy a laptop from Anna's store. Jan login to the online store and purchase chose a laptop. Anna sends him an identity request to ask for a verified address where to send the goods. Jan's `Digital wallet` received this request, display on screen who and what is asking for (use `user_address` schema with consent overlay and sensitive overlay to communicate about PII). Jan accepts the consent and `Digital wallet` pulls `user_address` schema from defined data vault and send the information to Anna in a form of Verifiable Claim signed by Jan's `Post`

2) Anna & PDC Inc
Anna wants to send goods to a specific customer, she priory received `user_address` schema which she sends to `PDC`. `PDC` can verify that address if is valid and that they are able to deliver that package.

3) Jan & Krzyś & Post
Krzyś is doing research about the population within the given city. He is sending a request to `Post` to help him out asking if they would like to ask their customers who are living within Vienna if they would like to take part in this research. `Krzyś` is using publicly available `user_address` schema with subset overlay to hide all attributes with exception of City name. 
`Post` sending the request to `Jan` with identity request from `Krzyś`. Where `Jan` needs to reveal the only city from his `user_address` schema. Since `Jan` is not available at the time of the request, the request is sent to his Sovrin Agent. 
Sovrin Agent received request about specific `user_address` schema and checks that `Jan` consent on being part of any public research helping to improve our society and sends back to `Krzyś` Agent proper information requested by `Krzyś`

# Why not to use?

* Why not use mixins?
* Why not use json-ld?
* Why not use xml/xlts?
* Why use it at all?
