# SVM_ImageClassificatio

SampleImages_classify.py::

The model takes jpeg images and attempts to classify each image as depicting a day- time scene or a night-time scene. 
Both the list and the images are stored in Google storage buckets.

Deliverables --
  1)To build a web server that uses standard HTTP request/response protocols to receive from the user
    a. User name
    b. Google storage bucket name (for a bucket containing N jpeg images)

  2)Upon receiving this information, the server generates a unique ServiceID and starts
    processing the images in the bucket one by one. For each image, the server will invoke the machine learning code to decide if it is a day-time scene or a night-time scene.
    a. The server responds with the ServiceID as an HTTP response to the service request.
    b. The server does not return any messages upon completion of the service

  3)The entire service (web server and machine learning code) must be deployed as a singleDocker micro-service in one virtual instance of the Google Cloud Platform

  4)Once the server finishes processing the set of N images, the server uploads the results to a MySQL database.
    a. The MySQL database can exist in the same or a separate virtual machine in the
       Google Cloud Platform.
    b. The MySQL database must be an external resource to the Docker container that
       hosts the web service.

   5)A single record in the database will have the following fields:
    a. ServiceID – A field that uniquely identifies the service. The web server generates this value upon receiving a service request. The format of this field must be a sequence of 8 characters selected randomly from:
    b. ServiceStartTime – The time when the service starts processing the first image in the bucket
    c. Status – The value of this field must be:
        i. ‘started’ when the service starts processing the first image,
        ii. ‘finished’ when the service finishes processing the last image
    d. ServiceEndTime – The time when the service finished processing the last image in
    the bucket


Results – 

A string containing a JSON message similar to the example shown below.
JSON example:
{"serviceResults": {
"UserName": "Michael Jordan", "ServiceRequestDate": {
"year": "2017", "month": "December", "day": "29",
"time": "18h45m"
},
"ServiceId": "BK98GPW5",
"Bucket": "User_selected_bucket_name", "Results": [
} }
Deliverables
{"image": "mypic1.jpg", "result": "day"}, {"image": "mypic2.jpg", "result": "night"}, {"image": "mypic3.jpg", "result": "night"} ]
