############
API usage
############

Hi there this Section of the documentation is to help us understand how to make requests to this API.


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







