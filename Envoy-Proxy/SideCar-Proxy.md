A sidecar proxy is an application design pattern which abstracts certain networking features, such as inter-service communications, monitoring and security, timeouts, retries, 
circuit breaking, communication protocols, away from the main architecture to ease the maintenance of the application as a whole.

Why SideCar pattern exists?
Problem: Library patterns in C# , DLL library and you can consume methods. We have client libaray for JAVA and server library say NodeJS since if its Rest API call, HTTP there has to be server.
In order to talk to server i.e. make HTTP req GET/POST, you need to import java HTTP Client library and make use of methods to communicate with backend server.

It's cool, what if you wanted to add timeout or HTTP-2 , if you want to implement it, then you need to write code for HTTP-2 using some library on both client and server in their respective langauages and framework.
None of this is your application, but networking.
You need to take care of all multiplexing, a thick application is made. A bug is made, you need to compile your JAVA apl, wasting your time writing networking. Next time HTTP-3 comes, lot of duplicate work.

https://www.youtube.com/watch?v=g7WeY0DZNJ0

We can take advantage of proxying,
All these features hold it into a bubble of your application. On client say HTTP-2 Proxy and on server, HTTP-2 Reverse Proxy. All you need to do, is spin up networking application (proxy server) and allow it to listen to port where HTTP host is running
Specify, every single L7 HTTP req to destination will first go to proxy server in yaml.
SideCar proxy will make request on your behalf.

Spin up {sidecar proxy .. is an appl} as reverse proxy on server side, and send req to reverse proxy appl, reverse proxy appl, makes a req on its behalf to NodeJS server. Its very easy to chnage format from JSON to protocol buffer & proxy application has no idea.
Usually, proxy and reverse proxy sidecar live in two different containers in the same host.

With microservices arch, sidecar pattern blew up. Service Mesh as a result became very popular e.g. istio, envoy, linkerd.

SideCar Containers/Proxies must be L7 proxy. They must look into your data. Else, how can they do service discovery, timeouts, etc.
Pros
- Language agnostic (polyglot) arch:- You can pick any lang you want. Networking layer is seperated, Make HTTP-1.1 req to sidecar proxy. It will take care of your conf.
- Protocol upgrade :- HTTP-1.1 can be upgraded to HTTP-2 and use gRPC & take care of bidirectional, mulitstreaming models.
- Security :- Build security features in proxy. Controlpane in Istio.
- Tracing and Monitoring :- Trace a call using unique identification, take logging, and produce grafana dashboard. 
- Service Discovery
- Caching :- Because its proxy, inherits benefit of caching. 
Cons
- Complexity :- of implementation. Microservices adds complexity and latency. Changing from library pattern to network calls (microservices), you are more prone to failures. Add two more sidecar containers to prevent it.
- Latency :- 

Kubernetes would manage these hell lot of microservices.

