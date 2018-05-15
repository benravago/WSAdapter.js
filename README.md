# WSAdapter

Yet another javascript SOAP client.  This one is an Ecmascript 6 rewrite of a javascript library I had written for some legacy AXIS 1.4 application.  The single script file is in interop/WSAdapter.js.  The interop/test.html file shows basic use of the WSAdapter functions.

### How to test using the Axis 1.4 SimpleAxisServer

1. Checkout the WSAdapter repo, cd into the WSAdapter directory.

2. Download an Axis 1.4 archive from one of the [apache mirrors](http://axis.apache.org/axis/java/releases.html) and extract the axis-1_4/{lib,samples/echo} directories.

3. The axis-ant.jar and log4j* files are not required for the demo so you can remove them.

4. Download javax.activation and javax.mail jars and move them to the axis-1_4/lib directory.

5. Start SimpleAxisServer with <code>**./server start**</code>.  When the server is ready you should see this message:
```
  INFO: starting up SimpleAxisServer on port 8080 (...)
```
6. The first time the server is started, you will need to deply the 'echo' application with <code>**./server deploy**</code>.  When the deploy is done you should see these messages:
```
  Processing file ./samples/echo/deploy.wsdd
  <Admin>Done processing</Admin>
```
7. Point your browser to http://localhost:8080/axis/services to verify that the Axis service is ready.  Clicking on the *'echo (wsdl)'* link should show you the WSDL for the 'echo' application.

8. Get the test.html page with http://localhost:8080/interop/test.html. The page is very basic.  You can run a test by selecting it from the dropdown.  The top textarea shows a javascript snippet that shows how the WebService operation is called and the expected return value.  If the test succeeds, then the icon should show a check mark, and a cross mark if it fails.

### Notes:

1. The most likely source of the javax.activation and javax.mail jars will be from public maven repositories. Try [mail/1.4](http://central.maven.org/maven2/javax/mail/mail/1.4/) and [activation/1.1](http://central.maven.org/maven2/javax/activation/activation/1.1/).

2. The tests in interop/test.html are based on the java code from samples/echo/TestClient.java.  Some tests will fail (echoMap, echoMapArray,echo2DStringArray,echoNestedArray) since these require additional support for 'xsd:anyType' and nested array elements.  I'll probably get around to these eventually, as time permits.



