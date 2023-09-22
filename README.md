# ApplicationServer

To run this application: 
- start a new netbeans project.
- copy all of the contents of this repo into the root directory of that project.
- compile the netbeans project.
- move the PlusOne.class, PlusOneAux.class and Fibonacci.class files into docRoot/appserver/job/impl
- in six terminal windows, cd into build/classes and run the following commands in this order (each in its own window): 

  `java web/SimpleWebServer ../../config/WebServer.properties`
  
  `java appserver/server/Server /../../config/Server.properties`
  
  `java appserver/satellite/Satellite ../../config/Satellite.Earth.properties ../../config/WebServer.properties ../../config/Server.properties`
  
  `java appserver/satellite/Satellite ../../config/Satellite.Mercury.properties ../../config/WebServer.properties ../../config/Server.properties`
  
  `java appserver/satellite/Satellite ../../config/Satellite.Venus.properties ../../config/WebServer.properties ../../config/Server.properties`
  
  `java appserver/client/FibonacciClient`
In the series of components that make up our application server, the satellite server is the most important one. Satellite servers are actually doing the work of the application server - the latter only being a way to access satellites. Thus satellites take on Jobs, get the right tool to do the job, process the job and get the results back to whoever requested the job to be done. In this context, the application server, which will be done in the next step, is really just adding value by (a) letting registering happen for satellite servers and (b) providing load-balancing based on some policy. That said, satellite servers can be run on their own, which comes in handy for this assignment as you can concentrate on the satellite server implementation, without getting side-tracked by the details and complexity of the overall application server structure.
