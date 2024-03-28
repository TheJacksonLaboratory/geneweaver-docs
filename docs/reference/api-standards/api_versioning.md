# API Versioning and Backwards Compatibility

!!! success "Overview" 
    In order to prioritize simplicity, reliability, and maintainability we seek to 
    **minimize the need for API versioning** _as much as possible_.

API versioning is a strategy to ensure that changes to the structure, 
features, or behavior of an API (Application Programming Interface) do not break 
applications that depend on it. APIs allow different software applications to 
communicate and interact with each other, so changes to an API can have broad impacts.

!!! tip
    If your service has a single client, **which you control**, then you can avoid
    versioning altogether. You also **do not** need to version APIs which have not yet
    been released. 

!!! warning 
    This document talks about versioning API deployments, a process that is separate 
    from application release versioning, which is described in the 
    [Software Versions Document](/Operations/Best_Practices/software_versions/).

    In the context of application release versioning, this document describes the 
    process of incrementing the **major** version number. For example, going from
    `v1.0.0` to `v2.0.0`.


## Guiding Principles

1. **Minimal versioning**: We avoid versioning unless absolutely necessary. This
   approach reduces complexity, both for the team developing the API and for those who
   consume it. We strive, whenever possible, to make changes that are backwards
   compatible.

2. **Independent changes for reproducible science**: To support reproducible science,
   it's essential that we can modify APIs without impacting the analysis. This principle
   allows us to evolve our systems independently, providing robustness and flexibility.

When versioning becomes unavoidable due to changes that can break existing clients, we
should follow the strategies provided in
this [guide](https://www.xmatters.com/blog/blog-four-rest-api-versioning-strategies/).

!!! danger
    Versioning is not a substitute for good API design. We should always strive to
    design APIs that are flexible and extensible, and that can evolve without breaking
    existing integrations. **Incrementing a major version should be a last resort.**


## Backwards Compatibility

Backwards compatibility is as important as versioning. By maintaining backwards
compatibility, we allow API consumers to upgrade at their own pace without breaking
their existing integrations. Strategies to ensure backwards compatibility include:

1. **Adding new fields**: When adding new data, do so by adding new fields that older
   clients will simply ignore. The simplest way to do this is to add new fields that 
   have a default value. 

2. **Avoid removing fields**: Removing data fields may break existing integrations. It's
   safer to deprecate old fields and leave them in place, while encouraging clients to
   use new fields.

3. **Keeping old endpoints**: If creating a new version of an endpoint, consider keeping
   the old one for a time to allow clients to transition gradually.

4. **Communicating changes**: Whenever a change is made that affects the API, it's
   important to inform consumers in advance to give them time to adapt.


## Service Information Endpoint

A service information endpoint is a valuable tool in API design, especially in terms of
API versioning and backwards compatibility. The service information endpoint provides a
clear way for client applications to understand the current state of the service, its
capabilities, and its versioning details. This enables clients to interact more
intelligently and efficiently with the service, adjusting their behavior based on the
information returned by this endpoint.

Here's how a service information endpoint contributes to API versioning and backward
compatibility:

1. **Communicating Version Information**:
   The version of the API is often part of the service information. This makes it clear
   to any consumers of the API what version they are interfacing with. Consumers can
   then decide how to handle any changes based on the version information. This is where
   an application would provide its deployed
   [Software Version](/Operations/Best_Practices/software_versions/) number.

2. **Facilitating Backward Compatibility**:
   By communicating what features, workflows, and filesystem protocols are supported by
   the service, a client application can adjust its behavior to only use features
   supported by the current API version. This allows older clients to still function
   correctly, even if new features or changes have been introduced in the latest version
   of the API.

3. **Providing Useful Metadata**:
   Additional information such as the name, description, environment, and contact
   details helps clients understand more about the service. For instance, it can help
   debug issues (e.g., if the environment is "test", the behavior might be different
   from a production environment).

4. **Allowing Intelligent Client Behavior**:
   In a more advanced use case, a client application might use the service information
   to decide between different APIs or services. 

## When We Need to Version

Despite our minimal versioning philosophy, there may be situations that require it.
These could include major architectural changes, the addition of new features that
aren't compatible with the current API design, or the nature of the system that's being
changed. 

In these cases, we should follow the versioning strategies outlined below.

### Versioning Strategies

When we need to introduce versioning, you might consider adopting one of the following
strategies:

1. **URI Versioning**: In this strategy, the version information is included in the URI
   itself. This is very simple and straightforward, but it can break URI consistency and
   may cause confusion.

      1. **URI Path**: This option involves including the version number as part of
         the URI path. This allows clients to cache resources easily, but requires 
         branching the entire API when incrementing the version.

      2. **Query Parameters**: This option involves including the version number as a
         query parameter. This is straightforward to implement, but can become 
         difficult to manage across multiple endpoints. It also requires maintaining
         all versions of the endpoints in a single application build.

2. **Request Header Versioning**: This approach keeps the URI clean and includes the
   version information in the request header. This preserves URI consistency, but it
   requires consumers to add version information to their requests.

3. **Media Type Versioning (Accept Header)**: This strategy requires the client to
   specify the version in the Accept header. It offers clean URIs, but it may increase
   complexity for clients.

4. **Hypermedia As The Engine Of Application State (HATEOAS)**: This is the most complex
   strategy, but it provides a lot of flexibility. It allows API consumers to navigate
   APIs through hypermedia links.

Remember, the choice of versioning strategy should be informed by our guiding
principles, the needs of our API consumers, and the nature of the changes that require
versioning. You should pick the strategy that best fits the situation of your 
application and it's needs, and prioritize minimizing API versioning as much as 
possible.

!!! tip
    For more information on possible versioning strategies, see this
    [guide](https://www.xmatters.com/blog/blog-four-rest-api-versioning-strategies/).