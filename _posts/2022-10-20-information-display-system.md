---
layout: post
published: true
title: 'Information Display System '
date: '2023-06-02'
---
## Information Display system for Rail/Flights/Ships and what not 

We have seen it multiple times, the flashing flight numbers on screen telling the status of flight or rail which is about to depart, there is a lot that goes on behind it and a lot of systems work together to provide you that info, let me share a working solution which can be adapted for any industry using the free open source technologies. 

### High level components 

![fids.PNG]({{site.baseurl}}/img/fids.PNG)


Screens use the browsers to communicate to the Flight information server and bring real time flights info, the alerts are published by the websockets running on the client side which poll any messages from the flight information Server. 


Screens ==> Browser(With Sockets)==> Flight info/Management Server server ==> Flight info DB/External Systems 


### Current solution contains following functionalities 

High level features of this solution 


![fids_components.PNG]({{site.baseurl}}/img/fids_components.PNG)




The code in git repo contains two servers, one serves the static angular app for screens and second server is the backend nodejs server which hosts the apis and hosts the socket server as well. 

[https://github.com/bhishekarora/FIDS](https://github.com/bhishekarora/FIDS)



![fids_arch.PNG]({{site.baseurl}}/img/fids_arch.PNG)


The flights arrivals and departures API are currently served via the data folder **node-js-server\app\data**
but this json data can be injected by any of the external services as per your use case, just call the API and use the flights array to push data back to the client.



All the screens can be controlled by backend Admin server and use JWT for authentication and use local screen browser storage to store tokens and authentications. 

Advertisements can be mapped to specific screens and content can selectively be mapped to specific screens.


### Advantages of this solution 

- Its built on Open Source stack :)
- Its Scalable, at presentation and backend layer, single VM hosting backend can serve 20 screens.
- Its built of on open source tech, Angular/Node/Mysql 
- It can support advertisements so you can earn from advertisers
- It has universal API support, so bring data from any of the systems and plugin 
- Its cloud ready, just spin a VM on cloud and configure your screens to point to the Flight info server.




This solution is easily customizable to work with any of the industry, rail , maritime etc.

I built it from scratch, would appreciate if you let the credit not in README intact.

If anyone needs help in modifying or enabling some integration from other systems  ping me on 

arora.abhishek@outlook.com
