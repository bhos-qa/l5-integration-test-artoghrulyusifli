I will try to explain what did I understand from the concept of integration testing

# What is integration testing ?
Integration testing is done to test the modules/components when integrated to verify that they work as expected i.e. to test the modules which are working fine individually does not have issues when integrated.When talking in terms of testing large application using black box testing technique, involves the combination of many modules which are tightly coupled with each other. We can apply the Integration testing technique concepts for testing these types of scenarios.

# Why Integration testing is important ?
As the name implies, integration testing is the process of testing individual components to see how well they perform conjoined. These components are combined to better understand multiple modules operating as a single unit.

# SETUP
In my Project I used Springboot framework in order to make the Integration testing.After I created the project I added the Springboot framework to this project.Consequently, i started to write sprinboot application and  integration testings for endpoints using the mockapi.io. A mock API server or mock server API imitates a real API server by providing realistic mock API responses to requests

```
    public void integrationTest(String url) {
        RestTemplate restTemplate = new RestTemplate();
        ResponseEntity<String> response = restTemplate.getForEntity(url, String.class);

        assertNotNull(response);
        assertTrue(response.getStatusCode() == HttpStatus.OK);
        assertEquals(MediaType.APPLICATION_JSON, response.getHeaders().getContentType());
        assertTrue(isResponseJSONValid(response.getBody()));
    }
```
The aim of the code above is include intergration testing to our project  by involving  a HttpEntity that contains headers which helps this entity to send GET request .
![image](https://user-images.githubusercontent.com/71690701/194750402-8f59148f-5d0a-469b-a56b-377094d532aa.png)

**Image 1.1 Creating Springboot application**

![image](https://user-images.githubusercontent.com/71690701/194750354-338b4736-1390-43ee-8274-ca21f5ec1023.png)

**Image 1.2 Using mockapi.io**

Also we need to setup our plugins ,dependincies and necessary execute permission for ./gradlew in build.gradle file:
![image](https://user-images.githubusercontent.com/71690701/194759055-17b0a567-b5fa-45f3-9f87-d9b2ede051bb.png)

After implementing integration testing I tested it to see if our integration tests are seccesful.For it I run the Springproj1Applicationtests :
![image](https://user-images.githubusercontent.com/71690701/194751414-53de24fb-3558-451b-95d0-1dbe531a57dd.png)

![image](https://user-images.githubusercontent.com/71690701/194750454-0c0fe321-1018-40a4-bf97-b0c4a8e434a1.png)
As we can see from picture all our integration testings passed test succesfully.
