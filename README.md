# jwt-spring-security
JWT Generation and Validation using Spring Boot + Spring Security

Following tutorial from https://www.javainuse.com/spring/boot-jwt

2 operations are happening in this project:
Generating JWT - Expose a POST API with mapping /authenticate. On passing correct username and password it will generate a JSON Web Token(JWT)
Validating JWT - If user tries to access GET API with mapping /hello. It will allow access only if request has a valid JSON Web Token(JWT)

Demo:

GET to localhost:8080/hello
response code 401 Unauthorized
----------------------------------------------------------------
Post Request to localhost:8080/authenticate

no headers except for 'Content-Type' -> application/json

request body:
{
"username" : "javainuse",
"password" : "pass" <----- this is incorrect password
}

response:
observe log message: "JWT Token does not begin with Bearer String"
response code 401 Unauthorized

----------------------------------------------------------------
Post Request to localhost:8080/authenticate

no headers except for 'Content-Type' -> application/json

request body:
{
"username" : "javainuse",
"password" : "password" <----- this is correct password
}

response:
{
    "jwttoken": "eyJhbGciOiJIUzUxMiJ9.eyJzdWIiOiJqYXZhaW51c2UiLCJleHAiOjE1NjExNTUyNjYsImlhdCI6MTU2MTEzNzI2Nn0.aMc0G-SYLiO5DAIKup_xhVyPsYao0dKJVvVC3-5kJVCIpvw_c4vKG9FZI-yb5dyf-vWTZKJNFDyG1clMh_7Nrg",
    "token": "eyJhbGciOiJIUzUxMiJ9.eyJzdWIiOiJqYXZhaW51c2UiLCJleHAiOjE1NjExNTUyNjYsImlhdCI6MTU2MTEzNzI2Nn0.aMc0G-SYLiO5DAIKup_xhVyPsYao0dKJVvVC3-5kJVCIpvw_c4vKG9FZI-yb5dyf-vWTZKJNFDyG1clMh_7Nrg"
}
response code 200 OK


GET to localhost:8080/hello
headers:
Authorization -> Bearer eyJhbGciOiJIUzUxMiJ9.eyJzdWIiOiJqYXZhaW51c2UiLCJleHAiOjE1NjExNTUyNjYsImlhdCI6MTU2MTEzNzI2Nn0.aMc0G-SYLiO5DAIKup_xhVyPsYao0dKJVvVC3-5kJVCIpvw_c4vKG9FZI-yb5dyf-vWTZKJNFDyG1clMh_7Nrg

Response Body:
"Hello World"
response code 200 OK