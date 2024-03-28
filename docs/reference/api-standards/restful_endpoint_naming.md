# RESTful API Endpoint Naming Standards

!!! success "Overview" 
    The RESTful API Endpoint Naming Standards are a set of guidelines we follow 
    to maintain **consistency**, **clarity**, and **usability** in our APIs. 

Application Programming Interfaces (APIs) act as the gateways to data and capabilities 
of our applications. With the REST architectural style, we can create scalable APIs that
are easy to consume and understand. 

Following a set of established naming conventions helps us create APIs that are 
straightforward to use, which in turn accelerates development, minimizes the risk of 
errors, and makes our services easier to consume.

!!! tip
    Although these are presented as standards, they should be considered as guidelines. 
    In specific cases, there might be valid reasons to deviate from these standards. 
    However, any deviation should be carefully considered and thoroughly discussed 
    within the team.

## Guiding Principles

1. **Resource Identification**: RESTful APIs use nouns (not verbs) to identify resources
or collections of resources. For example, use `/users` not `/getUsers` or `/createUser`.

2. **Consistency**: Maintain consistent naming conventions across the API. This reduces 
ambiguity and increases usability.

3. **Plural Form Resources**: Resources should be named in plural form, such as `/users`
rather than `/user`.

4. **Hierarchical Relationships**: Use sub-resources to show relationships between 
resources. For example, to get a user's comments, you can use `/users/{id}/comments`.

5. **Lowercase Letters**: Use lowercase letters for resources and collections. Mixed 
case or camelCase can lead to confusion and errors.

6. **Avoid Underscores (_)**: Underscores can sometimes be interpreted as spaces in 
certain contexts and should be avoided. Use hyphens (-) for better readability if 
needed[^2].

7. **No Trailing Slashes**: Trailing slashes should be avoided. For example, use 
`/users` not `/users/`[^1]. 

8. **Non-CRUD Functions**: For routes that don't easily map to CRUD operations (Create, 
Read, Update, Delete), consider mapping these to HTTP methods in a sensible way, or 
group them under a sub-resource. For example, `/users/{id}/activate`.

9. **Filters, Sorting, and Pagination**: For large collections, these should be 
expressed as query parameters. For example, 
`/users?status=active&sort=-registered&page=2`.

10. **HTTP Status Codes**: Use appropriate HTTP status codes to indicate the status of 
the request. For example, '200' for successful GET requests, '201' for successful POST 
requests, '400' for bad requests, etc. 

    !!! success "HTTP Status Codes"
        For more information on the correct status codes to use, see the response 
        status codes section of the 
        [HTTP Standards page](/Development/Best_Practices/API_Standards/http_standards/#http-response-status-codes).

11. **Error Handling**: Always return meaningful error messages and codes, helping the 
consumer understand what went wrong and how they might fix it.

!!! warning
    Remember that these are **guidelines**, not hard rules. They serve as a starting 
    point for the API design, but each API has unique needs and may require certain 
    exceptions or adaptations. Always prioritize clarity, simplicity, and usability 
    when designing your API.

## When Exceptions are Required

Despite these guiding principles, there may be situations that require exceptions or 
deviations. These could include compatibility with legacy systems, specific requirements
of certain clients, or other unique constraints.

In such cases, exceptions should be carefully considered, thoroughly discussed within 
the team, and clearly documented to avoid confusion and ensure everyone understands the 
reasons behind the deviation.

Always consider the potential impact of any exceptions on the overall usability, 
clarity, and consistency of the API, and strive to minimize such deviations as much as 
possible.


[^1]: [RFC 3986 - Uniform Resource Identifier (URI): Generic Syntax](https://www.rfc-editor.org/rfc/rfc3986#section-3.3)
[^2]: [StackOverflow - Hyphens, Underscores, or Camel Case](https://stackoverflow.com/questions/10302179/hyphen-underscore-or-camelcase-as-word-delimiter-in-uris)