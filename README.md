# springboot-oauth-server-poc
Oauth2 Authorization Server with multiple clients

1. First Aplication is Spring Boot app using spring boot 3.1.3 and maven and java 17 which acts as Spring Authorization Server.
 Should use latest maven artifact spring-boot-starter-oauth2-authorization-server. 
  Should run on port 9000. 
  This authorization server should use InMemoryUserDetailsManager having 2 users: 
   1st username is simpleuser with password 12345 and role USER. 2nd user adminuser with password 12345 and role ADMIN.
 There should be 3 clients for different application types:
- client_spa: for angular app, this client should have client-secret="secret" and should use Grant Type = PKCE Enhanced Authorization Code
- client_serverapp: for server side app, this client should have client-secret="secret" and should use Grant Type = Client Credentials
- client:mobile: for mobile app, this client should have client-secret="secret" and should use Grant Type = Authorization Code



2. Second app is Spring Boot based api using using spring boot 3.1.3 and maven and java 17 which acts as resource server. 
Should run on port 8080. Should use latest maven artifact spring-boot-starter-oauth2-resource-server.
This api should have following endpoints:
- GET /info: this is public endpoint
- GET /hello: this is protected end point, requires any authenticated user
- GET /hello-admin: this is protected end point, requires authenticated user with role ADMIN



3. Third app is springboot console app using using spring boot 3.1.3 and maven and java 17.
 Should run on port 8081. Should use Client Credentials for authentication(client_serverapp).
 This app should invoke "GET /hello-admin" endpoint on resource server and print response in the console.



4. Fourth app is angular or vue.js app which should have logging page with username and password which point to Spring Authorization Server to obtain jwt token.
 Should use PKCE Enhanced Authorization Code(client_spa).
 After succesfull login client should be rendered home page having 2 buttons:
- button 1 with title "hello" which will invoke api endpoint of resource server "GET /hello" and print response in the console
- button 2 with title "hello-admin" which will invoke api endpoint of resource server "GET /hello-admin" and print response in the console

