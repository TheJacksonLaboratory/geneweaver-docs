# DNS Naming

DNS (Domain Name System) is a system that translates human-friendly domain names, like 
`www.jax.org`, into the numerical IP addresses needed for devices to load Internet 
resources. This conversion process is often referred to as DNS name resolution, and it's
carried out by DNS servers. DNS serves as a sort of phonebook for the Internet, allowing
us to use memorable domain names while computers and other devices can handle the 
underlying IP addresses they correspond to.

Consistent DNS naming is important to maintaining API standards, both in terms of
operations and development. Consistent naming conventions enhance ease of use and 
understanding of APIs, as intuitive and uniform naming conventions allow developers to 
guess the correct endpoint, thereby reducing reliance on extensive documentation lookup. 
Furthermore, DNS naming conventions enhances efficiency in both development and 
maintenance as the risk of misconfiguration and mistakes drops when there 
are standard conventions to follow in handling APIs. Another aspect is interoperability;
standard naming conventions ease integration with other systems and services as they 
allow for a common language to be used. Finally, consistency in DNS naming aids in 
service discovery, particularly in a microservices architecture in that it streamlines 
categorization and comprehension of each service's purpose. 

## Naming Conventions
There is no single standard for DNS naming conventions that applications are _required_
to follow, however, the following is the default convention that should be followed
unless there is a compelling reason to deviate from it.

```
<application_name>-<environment>.<domain>.<tld>
```

Where most applications will be hosted on `.jax.org`
```
<application_name>-<environment>.jax.org
```

### Production DNS
For production environments, the application will also map a DNS name that **does not**
include the environment name. This is to allow for the use of the shorter DNS name
by most end users.

```
<application_name>.<domain>.<tld>
```

Where most applications will be hosted on `.jax.org`
```
<application_name>.jax.org
```

### Frontend Clients and Backend APIs
One important consideration is to maintain a list that maps client applications (e.g., 
web apps, CLI tools) to the backend services they employ. This also helps manage CORS 
settings, if needed. This also helps to make it clear when specific frontend clients are
siblings of specific backend APIs. 

Where possible, it is preferred that the frontend client uses the same DNS name as the 
backend API. This allows for intuitive discovery of the backend API by the frontend 
client, and by developers, quality assurance, and operations personnel.

!!! tip "Micro-service Architectures"
    In a world of micro-services it's likely that we would move away from a one-to-one
    mapping between a UI and an API. In theory services will be for specific purposes,
    while clients may become more broad and integrated, pulling from multiple APIs.

    Data or analytic API’s should also be concerned with serving up other programmatic
    clients, like scripts or Jupyter notebooks developed by an analyst.

### Versioning
Versioning should be handled by the application itself, and **not by the DNS name**.
This allows for the application to be updated to a new version without requiring any
changes to the DNS name.

!!! tip "Versioning Not Required"
    Not all APIs will require versioning, and those that do not should not feel 
    compelled to implement it. Often, versioning can be avoided by careful design of the
    API.

    Read more about API Versioning in the API Standards group's
    [versioning document](/Development/Best_Practices/API_Standards/api_versioning/).


### Environments
The environment name should be one of the following:

- `dev` - Development environment
- `sqa` - Testing environment
- `stage` - Staging environment
- `prod` - Production environment

It is highly recommended to deploy each of the above environments, especially if your
application will rely on other applications, or if other applications will rely on your
application. This allows for your application, and those that depend on it, to always
have a matching environment for each deployment environment.


#### Staging/Production
The staging and production environments are special environments that should be as close
to identical as possible. The only difference between the two should be the data that
they are using. This is to ensure that any issues that are found in staging can be
reproduced in production. 

Depending on your application deployment model, these two environments can be viewed as
the "Blue" and "Green" in a "Blue/Green" deployment model.

??? note "Blue/Green Deployments"
      Blue/Green deployments are a type of software release management strategy designed to 
      reduce downtime and risk by running two identical production environments known as 
      Blue and Green.

      - Blue environment: This is the live production environment that is currently serving 
        user traffic.
      - Green environment: This is the clone of the production environment where you deploy 
        the new version of the application.

      Initially, the Blue environment is live, serving all user traffic. When a new version 
      of the software is ready for release, it is deployed to the Green environment. 
      
      Once the new version is tested and ready to go live, the router is switched to direct 
      all incoming traffic to the Green environment. The Green environment then becomes the 
      live or active environment. 
      
      The Blue environment, now idle, can be used for preparation for the next release.


## Additional Considerations

1) Applications should be hosted on port 80/443 so that the user does **not** need to 
specify a port.
2) It's important to publicize if the application is hosted on an internal-only
IP address as this will affect the ability of users to access the application.
