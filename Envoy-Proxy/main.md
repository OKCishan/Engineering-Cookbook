Envoy: L7 Proxy and Communication bus, built at Lyft to move their monlith to microservices arch. (Ref: https://www.youtube.com/watch?v=40gKzHQWgP0)


One of applications of Envoy as servie mesh (which is basically proxy and reverse proxy at same time), prevents exposure of backend internal architecture. Others: Niginx, HAproxy etc.
You can configure Envoy to run on HTTP/2

Envoy Architecture:  { Documentation: https://www.envoyproxy.io/docs/envoy/latest/ }
1) Downstream (front of envoy i.e. client) /Upstream (anything/behind of envoy i.e. backend)
2) Clusters   (collection of hosts serving, we give a name, we set load balancing policy on cluster level)
3) Listeners  (FrontEnd, listen to a port)
4) Network Filters  (maps listeners to clusters e.g. TCP Proxy L4, HTTP Proxy, TLS termination / build your own filter by configuring yaml)
5) Threading Model  (single process multi-threaded application, not multiprocessing)
6) Connection Pools



 
