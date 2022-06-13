---
layout: post
published: true
title: 'Face is the new boarding pass, the low level design.'
---
## Implementing single token journeys with open source software


Face is your boarding pass, generate unique digital token specific to the traveller and use it across all your systems to enable seamless touchless travel.


![]({{site.baseurl}}/img/WeChat-Face-Recognition-1.gif)



## High Level Design

Passenger can enroll for this either via Mobile or the kiosk on the Airport.

Scan Passport/Face/Boarding pass --> Generate a unique token for journey and check that token at different stages of travel.


![]({{site.baseurl}}/img/high.png)


## Low level Design

Passenger shows the Passport at the kiosk scanner (Scan MRZ- Machine Readable Zone - [Free Library](https://github.com/patrick-randria/passport-reader) ) 

Passenger shows the face and a face mask array is created for that face, use the [free face recognition library](https://github.com/ageitgey/face_recognition) built on open CV ( Accuracy is high) ..

The face mask vector array is used for face encodings, just save the enodings via pickle and save it on disk and load when required for comparisons. (Check out the [post](https://stackoverflow.com/questions/59004129/storing-a-list-of-face-encodings-in-python-for-face-identification))
![]({{site.baseurl}}/img/12.gif)

Now we have the data available for Passport and face mask, its time to get the boarding pass QR code.

Use this free [library](https://github.com/zxing/zxing) to get the details out of QR code (pdf 417 format for boarding pass- 2d bar code)

Its time to create the single token, the digital identity of traveller.

Just take the information from Passport+Face encoding+ Boarding pass +Salt( may be time stamp(optional)) ==> ****TOKEN****



Now out token is available, time to save it on our single token platform so that other systems can use it. 

Lets use MongoDb/Python stack for our single token platform and create an API end point called ./CheckFace


User ==> Kiosk ===Enroll==> Token generated ==>Inserted in Mongo DB==>Available for verification on Endpoint (./CheckFace) running Python flask 


![tech.PNG]({{site.baseurl}}/img/tech.PNG)


Rest of the systems on the airport can use their own open cv implementation (java/python/.NET) and capture live faces and compare with the encodings in the picklized mongo db. 

The token can be alive till the departure and later we can destroy the token from identity platform and let it remain in our db for reporting and other use cases. Facial data can remain in system for future as we need not enroll the passengers again if they travel in future, we can use the old facials and generate a new token for travel for that passenger. 

The face masks stored can also be very usefull for future machine learning to improve operational efficiencies on the airport, e.g passenger flow modelling. 


If you need any assistance implementing this reach out to me on 

![qr.PNG]({{site.baseurl}}/img/qr.PNG)





















