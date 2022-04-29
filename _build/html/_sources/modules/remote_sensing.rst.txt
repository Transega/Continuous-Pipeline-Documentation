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

*Landsat 8 has a sixteen days revisit time, meaning we can get images after every concsecutive 16 days*

.. figure:: ../Images/sensorlandsat_param.png
   :alt: 

sensors available for Landsat 

    ii. Sentinel 

Sentinel has sentinel_2 in this implementation

*Sentinel 2  a six days revisit time, meaning we can get images after every concsecutive 6 days*

.. figure:: ../Images/sensor_param.png
   :alt: 

sensors available for Sentinel

c. product

Once we have a sensor selected we use the images to compute products:

    i. Normalized Difference Vegetation Index (NDVI)

It is arrived at by indexing the Near infrared and the red band from a satelite Image,
it is a proxy that informs whether or not Vegetation is healthy.

    ii. Normalized Difference Moisture Index (NDMI)

The product is arrived at by using Near infrared and Short wave infrared bands from a satelite Imagery, 
it is a proxy for estimating whether or not the crop is water stressed.

**Sentinel_2 has the two products (NDVI and NDMI) while L8 has only NDVI as at now**


.. figure:: ../Images/product_landsat.png
   :alt: 

Products available available for L8

.. figure:: ../Images/products_sentinel.png
   :alt: 

Products available available for sentinel_2

d. geometry

*The geometry parameter is the boundary layer or the are of interest that the satelite image should fall within*

*In this case the feature collection that we obtain from the backend, instead of providing the actual feature collection we 
provide a name of the specific administrative layer and the system will auto generate the feature collection and use it to do the 
analysis from the backend*


* If we need a county we specify a parameter county and supply the name

* If we need a sub-county we specify a parameter sub-county and supply the name

* If we need a ward we specify a parameter ward and supply the name

e. dates 

The dates are used to filter the period within which the satelite images should fall,
in this case the system takes the start date and the end date generates bi-weekly dates that fall within that 
period and computes the long-term median and the bi-weekly products. 

    i. start date 

    ii. end date 

The date parameter can be left blank the system will auto-generate by taking the current date as the end date while,
it calculates 30 days earlier than the current date as the start date

The start date has to be less than the end date otherwise the system will throw an error

.. figure:: ../Images/dates.png
   :alt: 

Dates 


Connecting the Dots 
-------------------

Making the api request for remote_sensing data would be as follows 

a. provide the parameters;

    i. the platfom

    ii. the sensor

    iii. the product

    iv. geometry 

    v. start date 

    vi. end date 


**Note the geometry will either be county, sub-county or ward**


*The request is made as follows:* 

* county request

``http://208.85.21.253:8080/RemotesensingApi/get_rsAdmi1/?platform=Sentinel&sensor=Sentinel_2&product=NDVI&start_date=2021-01-01&end_date=2021-05-30&county=Uasin Gishu``

.. figure:: ../Images/countyrequest.png
   :alt: 

County RS request

* sub-county request 

``http://208.85.21.253:8080/RemotesensingApi/get_rsAdmi1/?platform=Sentinel&sensor=Sentinel_2&product=NDVI&start_date=2021-03-01&end_date=2021-04-22&subcounty=Mogotio``


* ward request 

``http://208.85.21.253:8080/RemotesensingApi/get_rsAdmi1/?platform=Sentinel&sensor=Sentinel_2&product=NDVI&start_date=2021-03-01&end_date=2021-04-22&ward=Emining``



*The response from the api contains, image url which is an object with an array of objects that have the time and the image url,it also have time series which is an object with an array of object with time and index values (NDVI or NDMI), the time is in system time stamp* 




