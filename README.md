# AI-Real-Estate-Valuation
Property valuation tool for unlisted homes using a variety of tools and software stacks in awesome group project :)

THIS REPRESENTS A CLOSED REPOSITORY

Check out the demo at:  https://ai-real-estate-valuator.herokuapp.com


## Introduction
The purpose of this project is to predict the current value of unlisted properties in the Toronto region based on a 30+ variable multilayer percepitron. The intention is then to visualize this on a web-application like a Python-Flask with react flask where you would be able to type in an address or postal code, and our pre-trained model would spit out a value.


## Data
The data for this project was retrieved using a Puppeteer webscrapper taking data primarily from zolo.com with over 14,000 properties in data pulled and which will be stored in a MySQL database. The geolocational data was then found by using a latlong.net where the Puppeteer scrapper simulates human behavior to the long, lat data.

### Variables
There were a variety of variables as mentioned taken into consideration for the MLP model:
* location
* type of property
* nearby amenities (i.e. nearest distance to schools, grocery stores etc.)
* Rankings of nearest schools

#### Location
This was a unique variable to take into consideration. The difference in prices of two properties incrases as the distance increases. This relationship follows a polynomial relationship fairly well. After standardizing our data, and removing outliers, our algothim runs to find a specific polynomial line of best fit for every single node in our DB. When loading our model a weighted average of these lines is taken following a standarized inverse proportionality function. This average is then used to caculate estimated deviation in the price according to the distance away each node is from the prediction point. Summing the averages in an inversely proprotion way, we have the average estimated error on our price prediction. The price prediction is done using the inverse proporionallity function afore-mentioned as well. 

Now we have a predicted price, and the estimated error on this price prediction done purle mathematically. 100 % - error is the percentage of utilization, which is what percent of our overall model location will make up. The rest will be done using our AI-Model, see next section:

### AI Model (Julius to complete) 


### Location Based Search Optimization and Declustering Algorithm

One difficult problem that needed to be conquered is filtering all of our data in a linear way by location. This requires some spherical geometry. As all location data is geo-encoded in lon and lat, an upper an lower bound of those two coordinates needs to be caclulated and used. Via some algebra done on the haversine formula which relates the surface area of a sphere to angles from the radius, we are able to find these max/min deviations as seen below:

![alt text](/reverse_haversine_mathematics.png "Logo Title Text 1")

