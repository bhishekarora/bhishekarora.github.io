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

Now we have the data available for Passport and face mask, its time to get the boarding pass QR code.

Use this free [library](https://github.com/zxing/zxing) to get the details out of QR code (pdf 417 format for boarding pass- 2d bar code)









