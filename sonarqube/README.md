### SonarQube - Basics for starting tests
---
### References:
* https://hub.docker.com/_/sonarqube
* https://hub.docker.com/r/sonarsource/sonar-scanner-cli
---
### SonarQube
Simulating a basic local code quality testing environment based on a quick introduction to sonarqube tools.


Sonarqube server:
```
docker run --name sonarqube-custom -p 9000:9000 sonarqube:community
```
After starting it, you must:
* Confirm a new password;
* Generate a local project;
  * Enter the name of the project;
  * Indicate the branch it will operate on -> It is worth remembering that the community only operates on one branch at a time;
* Specify the OS version you are going to run the action on.
* Finally, get the information needed to close the communication with the server and perform the tests;

Below is the information generated during the tests:
```
Analyze "test_php": sqp_3bc52977e378af57c5a96eaf796f18eeef468382

Estou usando o linux, então é esse o comando:
sonar-scanner \
  -Dsonar.projectKey=test_php \
  -Dsonar.sources=. \
  -Dsonar.host.url=http://localhost:9000 \
  -Dsonar.token=sqp_3bc52977e378af57c5a96eaf796f18eeef468382
```


For the tests, I set up a local directory to perform the tests in PHP. To perform the tests, here is a docker img that already obtains the local data to send for testing on the SonarQube server.

For this command to work, you need to feed it with the values ​​from the Sonar server project information and information and the server address:

```
docker run --network=host --rm -e SONAR_HOST_URL="https://localhost:9000" -v "./php_test:/usr/src" sonarsource/sonar-scanner-cli -Dsonar.projectKey=test_php -Dsonar.sources=. -Dsonar.host.url=http://localhost:9000 -Dsonar.token=sqp_3bc52977e378af57c5a96eaf796f18eeef468382
```
