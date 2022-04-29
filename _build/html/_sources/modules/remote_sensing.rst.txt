###################
Remote Sensing Data 
###################

Hi there this Section of the documentation is to help us understand how to make requests to this API for remotely sensed data from Google Earth engine Api.

base url **http://208.85.21.253:8080/**

Getting Remote Sensing Data 
---------------------------


*This end point it used to give Web Map service Url end point and statistics*

You only need to pass the parameters as follows:

a. platform 

*platform is the parameter that tells the system which satelite instrument we are 
interested in as per writting this documentation Landsat and Sentinel are the available platforms*

if a request is made and the platform parameter is not supplied the system will respond with the valid platfom parameters 
available 

.. figure:: ../Images/platform_param.png
   :alt: 

Platforms available

b. sensor

Every satelite has specific sensors mounted for various purposes; and each platfom will have different forms of sensors

    i. Landsat 

Landsat has L8 as the available sensor in this implementation 

.. figure:: ../Images/sensorlandsat_param.png
   :alt: 

sensors available for Landsat 

    ii. Sentinel 

Sentinel has sentinel_2 in this implementation

.. figure:: ../Images/sensor_param.png
   :alt: 

sensors available for Sentinel

