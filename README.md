Our projects architecture is comprised of three main components

A decible level detecting embedded device, a server and database and a front end web app

The embedded device was created using an ESP32 integrated development board, featuring a
WIFI chip and GPIOS used to connect a MEMS microphone. It was programmed using the ESP extension of the Arduino platform.
The embedded device detects decible levels
in its surroundings at a rate of .5hz and transmits the data to the server every 32 samples. The device
communicates with our server over WIFI using http requests, sending a json payload for entry into the database.
The device is small enough to fit inside a dental floss container and is powered using a micro usb cable.
The cost of each prototype at a consumer level is about $15 dollars, but mass production could lower to below
$3, likely much lower.

The server is a standard restful http server developed in nodejs using the expressjs server framework and MySql database. It
provides three functionalities. It accepts http requests for submitting noise observations from all extent devices
as well as serving back historical data upon request. Finally it also serves the front end client to web browsers.
Our server is hosted using heroku to run the server code, and jawsdb to host our mysql data.

Finally our front end web app requests and displays our data in easily viewable charts. The charts show to the minute
historical noise levels and updates by the minute real time noise observations. The chart also conveniently displays
noise threshold levels for easy identificiation of excessive volume levels. Additionally there is a reports page which
gives average noiselevels over a given time period as well as summary statistics. The web app was developed using reactjs for
the application framework and chartjs for displaying the charts. The data is accessed from the server using http requests.
