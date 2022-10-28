########################
Crop Calenda information 
########################

Overview 
--------

Crop calenda information is vital in the sense that it helps us track the crop growth cycle
in turn assess the vegetation status in terms of whether or not the crop is performing well.

A model was built in the backend to store this information, to help in automation of the process of crop 
performance evaluation.

A model in **django** implementation is the defination of the structure of the database, i.e the name of the fields and the type of data 
stored, whether or not a field can be null, the primary key field etc. 

This model currently has the following fields country_name, 
county_name, crop, stage, project_name, 
start_date and end_date.

The model can be further improved. 

The information is updated from the django admin page.

We get this information and compare with what a user request from the remote sensing api to establish the crop conditions
by applying some logic to be discussed later on this documentation.

Crop calenda api requests
-------------------------

i. Crops available

This api returns a list of the crops available, this is crucial in only allowing analysis for crops we have crop calenda information

**parameters**

* county 

supply the name of the country


``https://skyfall-pipeline.pula.cloud/CropCalenderApi/getCrops/?country=Kenya``


.. figure:: ../Images/cropscalenda.png
   :alt: 

Since we have county name we can query for crop list as per a particualar county, this however depends on 
whether the county has been added, in the event the county doesnt have data the api will return the default for the 
country. Moreover since crops may vary per project adding project parameter will help to 
filter only crops for that project. For example 

``https://skyfall-pipeline.pula.cloud/CropCalenderApi/getCrops/?country=Kenya&project=KCEP``

.. figure:: ../Images/crops_per_project.png
   :alt: 

*Crops available list*

Notice in the above request KCEP project does not have wheat crop 


ii. Crop calenda information

This api returns crop calenda information for a specific country and crop in question 

**parameters**

* country

name of the country

* crop 

name of the crop 

* project

name of the project 

* county 

county name (optional)

*The crop names is obtained from the available crops api for that country*


``https://skyfall-pipeline.pula.cloud/CropCalenderApi/getCrops/?country=Kenya&project=KCEP&crop=Maize``


.. figure:: ../Images/cropinfo.png
   :alt: 

Crop calenda information for Maize



