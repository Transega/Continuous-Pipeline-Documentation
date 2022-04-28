#####################################
API usage Administrative layers query
#####################################

Hi there this Section of the documentation is to help us understand how to make requests to this API.

base url **http://208.85.21.253:8080/**


Getting Admistration level Data
-------------------------------
*Admistration or administrative boundaries are layers we are using to map diffirent places 
they are basically shapefiles or feature collection and vary according to the levels*

* Admistration level zero (0)

This the country level dataset 

* Admistration level one (1)

This is the first level of administrative boundary for diffirent locations (*Jurisdiction*) 
the name varies in the case of Kenya they are refered to as Counties. 

    a. Counties list 
    
This county list is what the list of counties available for that country this is provided for from the back end by looping 
through the field in the database that contains the names.

That information is queried as follows 

``http://208.85.21.253:8080/AdminData/get_adm1_shapefile/?county_names=ALL``

The response is a json object with key **counties** and item is an **array** containing the names of the counties

.. figure:: ../Images/Admin1names.png
   :alt: API request for county names 

API request for county names

    b. County dataset

This api request returns the actual Geojson file given the county name 

Note **the name has to be in the array since the data is a query to the database.** It returns a feature collection

County Geojson is queried as follows:

``http://208.85.21.253:8080/AdminData/get_adm1_shapefile/?Get_county=Kisumu``

`` Get_county=`` the name of the county is placed after the **=** sign

.. figure:: ../Images/AdminGeojson.png
   :alt: API request for county feature collection

API request for county feature collection

* Admistration level two (2)

*Administrative level two in the Kenya context means the sub-counties or constituencies*

*There are the second leve of administrative boundary a number of administrative level two, forms a county*

    a. Sub-county list (admin 2)

The query is made giving a county name; the api returns list of names sub-counties (admin 2) within a county, the names recieved from Admin1names are used to query for the names for the
sub-counties 

county_name field of the ADM2DATA is filter and an iteration is done to the field of sub_county_names to get the names


**The Query is done as follows**
``http://208.85.21.253:8080/AdminData/get_adm2_shapefile/?Get_sub_counties_names=Nairobi``


.. figure:: ../Images/Admin2names.png
   :alt: API request for admin2 names 

API request for admin2 names


    b. Sub-County (admin2) dataset

This api request returns the actual Geojson file given the admin2 name 

Note **the name has to be in the array of sub_county_names since the data is a query to the database.** It returns a feature collection

**Admin 2 Geojson is queried as follows:**

``http://208.85.21.253:8080/AdminData/get_adm2_shapefile/?sub_county=Mogotio``

``sub_county=`` the name of the sub_county is placed after the **=** sign

.. figure:: ../Images/Admin2Geojson.png
   :alt: API request for sub_county feature collection

API request for sub_county feature collection


* Admistration level three (3)

*Administrative level three in the Kenya context means the wards*

*This is the third administrative boundary*

    a. Wards list (admin 3)

The query is made giving a sub-county name; the api returns list of names wards (admin 3) within a sub-county, 
the names recieved from Admin2names are used to query for the names for the wards 

sub_county_name field of the ADM3DATA is filtered and an iteration is done to the field of ward_names to get the names


**The Query is done as follows**
``http://208.85.21.253:8080/AdminData/get_adm3_shapefile/?Get_wards_in_sub_county=Mogotio``


.. figure:: ../Images/Admin3names.png
   :alt: API request for admin3 names 

API request for admin3 names


    b. ward (admin3) dataset

This api request returns the actual Geojson file given the admin3 name 

Note **the name has to be in the array of ward names since the data is a query to the database.** It returns a feature collection

**Admin 3 Geojson is queried as follows:**

``http://208.85.21.253:8080/AdminData/get_adm3_shapefile/?GetWardGeojson=Emining``

``ward=`` the name of the ward is placed after the **=** sign

.. figure:: ../Images/Admin3Geojson.png
   :alt: API request for ward feature collection

API request for ward feature collection










