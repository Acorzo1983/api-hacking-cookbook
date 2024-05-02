# API Analysis

## Types of APIs

### REST APIs
REST (Representational State Transfer) is an architectural style used for designing networked applications. It uses HTTP requests to access and manipulate data.

#### Key Characteristics:
- **Stateless**: Each request from client to server must contain all the information needed to understand the request, without taking advantage of any stored context on the server.
- **Resource-based**: Resources are identified by URLs, which provide a global addressing space for resource and service discovery.
- **Uses Standard HTTP Methods**: Such as GET, POST, PUT, DELETE, etc.
- **Data Formats**: Commonly uses JSON or XML to send and receive data.

### GraphQL APIs
GraphQL is a query language designed to make APIs fast, flexible, and developer-friendly. It allows clients to request exactly the data they need.

#### Key Characteristics:
- **Efficient Data Fetching**: Clients can specify exactly what data they need.
- **Single Endpoint**: Unlike REST, which uses multiple endpoints, GraphQL uses a single endpoint to handle all actions.
- **Type System**: Every data is associated with a type, which enhances validation and introspection.

## Authentication and Security

### Common Authentication Methods
Authentication is crucial for ensuring that interactions with your API are secure. Here are some commonly used methods:

#### API Keys
- **Usage**: Simple and widely used method for controlling access.
- **Security Considerations**: API keys can be vulnerable if exposed. Always use HTTPS to encrypt the API key during transmission.

#### OAuth
- **Usage**: Allows an application to authenticate on behalf of a user.
- **Details**: OAuth provides tokens instead of credentials to access their resources. It is widely used for its flexibility and security features.

#### JSON Web Tokens (JWT)
- **Usage**: Encodes JSON objects in a compact, URL-safe means of representing claims to be transferred between two parties.
- **Benefits**: It is self-contained, meaning it carries all the necessary information about the user or system performing the API call.

### Security Practices
Ensuring the security of your API involves more than just implementing strong authentication. Consider the following practices:

- **Encryption**: Use HTTPS to encrypt data in transit.
- **Throttling**: Protect against brute-force attacks by limiting the rate of incoming requests.
- **Access Controls**: Implement fine-grained access controls to ensure users can only perform actions they’re authorized to.

By understanding these fundamental aspects of API analysis, you can better prepare for the more advanced stages of API hacking and ensure robust security from the start.
