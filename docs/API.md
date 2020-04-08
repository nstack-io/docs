---
currentMenu: api-doc
---

# API 

The NStack API is open and you are welcome to build your own tools in case none of our open-source SDKs fits your needs. If you were to build your own SDK around NStack, we woud love to hear from you and curious to see what you built.

The full API documentation is available:

[Postman collection](https://documenter.getpostman.com/view/12675/S1a8yjgk)

[NSpec]

[Open Api 3.0](https://raw.githubusercontent.com/nstack-io/documentation/master/yaml/openapi3.0.yaml)*

\* Work in progress


## Q & A

#### What is a GUID?
A GUID (Globally unique identifier) is a unique identifier. It should be generated **once** and used in all future requests from the device.

The Nstack SDK will handle creation and storing of the guid on the device.  If you are using the API instead of the SDK  you can create your own GUID/UUID by using the UUID class in java (Universally Unique Identifier).

val uuid = UUID.randomUUID().toString() 

It is important that you only generate it once and store it otherwise features like ratereminder will not work. 


#### Should I use the NStack SDKs or access the API directly? 
Always prefer the available SDKs. If there is something the API offers that is not available in the SDK and you would like to use, please notify us and we will look into it. You are also very welcome to contribute to features and fixes to the codebase of the SDK for your platform. 

Using the API directly is more complex and we are trying to reflect all API features inside the SDKs. However, it is still possible that a newer feature has not made it to the SDK just yet so in such rare cases you might need to rely on a direct call to the API. You will also need to rely on the API in case there is no SDK for your platform. If you are willing to start a new SDK in that case, please let us know and maybe we can help!
