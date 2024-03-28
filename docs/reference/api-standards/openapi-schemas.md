# OpenAPI Schemas

!!! success "Overview"
    As part of our commitment to creating well-defined, reliable, and easy-to-use APIs, 
    we adopt OpenAPI[^1] as a standard tool for defining, creating, and documenting our 
    APIs. OpenAPI helps our teams collaborate more efficiently, enhances the developer 
    experience, and maintains the quality of our APIs. This document lays out standards 
    and best practices around the usage and publication of OpenAPI schemas.

## Why OpenAPI?

OpenAPI[^1] is an industry-standard method for describing RESTful APIs. By requiring an 
OpenAPI document[^2] for each API, we aim to:

- **Increase Transparency**: With an OpenAPI document, every aspect of an API is clearly
described, from endpoints to response formats. This reduces guesswork and the potential 
for misunderstandings.

- **Streamline Collaboration**: Frontend and backend teams can reference the OpenAPI 
document to understand what data is available, how to access it, and what kind of 
responses to expect. 

- **Simplify Integration**: Other systems or third-party developers can use the OpenAPI 
document to understand how to integrate with our APIs. 

- **Enable API Testing and Monitoring**: OpenAPI documents can be used to generate 
testing scripts and monitor APIs for any discrepancies in expected behavior.

- **Improve Developer Experience**: An OpenAPI document forms the basis for generating 
interactive documentation, SDKs, and API explorers, enhancing the overall developer 
experience.

## Key Principles

1. **Up-to-date Schema**: Each RESTful API must always provide an up-to-date 
`openapi.json` file, reflecting the latest version of the API. 

2. **Automatic Generation**: The `openapi.json` file should be automatically generated 
from the source code and annotations as part of the build pipeline.

3. **Public Accessibility**: The `openapi.json` file should be easily accessible, 
preferably through a dedicated endpoint (e.g., 
`https://api.yourdomain.com/openapi.json`).

4. **Auto-generated API Documentation**: The OpenAPI schema should be used to 
automatically generate and update API navigator pages or interactive API documentation 
(like Swagger UI).

## Detailed Standards

### OpenAPI File Generation

- Use tools and libraries that support OpenAPI file generation from code annotations 
(e.g., Swagger for Java or SpringFox). 

- The OpenAPI file should be generated as part of the build process. 

- Keep your annotations up-to-date as you make changes to your API.

### OpenAPI File Hosting

- The `openapi.json` file should be publicly accessible via a dedicated URL.

- The file should be placed at a consistent location across all APIs for easy discovery 
  (e.g., `https://api.yourdomain.com/openapi.json`).

- The server should deliver the `openapi.json` file with the correct MIME type 
`application/json`.

### Versioning

- The OpenAPI document should reflect the current version of the API and be updated with
each version change.

- If multiple versions of the API exist, each version should have its own `openapi.json`
file.

### Auto-generated API Documentation

- Use a tool like Swagger UI or ReDoc to automatically generate interactive API 
documentation from the OpenAPI schema.

- The documentation should be publicly accessible and updated automatically whenever the 
OpenAPI schema is updated.

- The documentation should provide interactive features such as the ability to send test
requests.

!!! info
    By adopting OpenAPI and following these standards and best practices, we can improve 
    the developer experience, enhance the discoverability of our APIs, and ensure our 
    documentation is always up-to-date.

[^1]: [OpenAPI Initiative](https://www.openapis.org/)
[^2]: [OpenAPI Specification](https://spec.openapis.org/oas/v3.1.0)
