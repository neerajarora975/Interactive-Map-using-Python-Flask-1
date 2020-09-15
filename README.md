# Interactive-Map-using-Python-Flask-1

Displaying an Interactive Map with Python and Flask - Part 1
 

Prerequisites

Python must be installed on your system and you require a Freemium account on developer.here.com.
You will also need an API Key from the Developer Portal (which we will use in the code). Simply sign up for your free account and generate API key on your account page.

Writing Python Code for Web Development
For seamless integration of Python with an HTML page we use Python based web frameworks, here we are using Flask, which is a simple and powerful micro-framework for web application development in Python.
Flask as a library can be downloaded using the following command:








pip install flask
Write the following code in a new python file:

	from flask import Flask,render_template
	app = Flask(__name__)
	
	@app.route('/')
	def map_func():
		return render_template('map.html')
	if __name__ == '__main__':
	    app.run(debug = True)    


The above code represents a simple flask template in which we have imported two sub-packages of flask, viz., Flask and render_template. Also, we have created a function called the “map_func”. This function returns a Jinja2 html page.
A HTML file will be required to show the Map on the browser. For this, we need to create an HTML file in a folder called “templates”, and then name the file as “map.html”.
In the <head> of HTML file, add the following <script> elements to load the API code libraries:
	<script src="https://js.api.here.com/v3/3.1/mapsjs-core.js" type="text/javascript" charset="utf-8"></script>
	<script src="https://js.api.here.com/v3/3.1/mapsjs-service.js" type="text/javascript" charset="utf-8"></script>


After this, we need to initialize the communication with the back-end services and initialize the map in the <body> of HTML inside the <script>:




	<script>
	      	// Initialize the platform object:
	      	var platform = new H.service.Platform({
	        'apikey': 'YOUR API KEY'
	      	});  
		
		const lat = 22.719568;
		const long = 75.857727;
	
		// Obtain the default map types from the platform object
	      	var maptypes = platform.createDefaultLayers();
	
	      	// Instantiate (and display) a map object:
	      	var map = new H.Map(
	        document.getElementById('mapContainer'),
	        maptypes.vector.normal.map,
	        {
	         zoom: 10,
	         center: { lat: lat, lng: long }  
	        });
			
		var marker = new H.map.Marker({ lat: lat, lng: long });
			
		// Add the marker to the map:
		map.addObject(marker);
			
	</script>


You can find detailed explanation of platform object and map objejct 
The complete HTML code looks like this:






	<html>  
	<head>
	<meta name="viewport" content="initial-scale=1.0, width=device-width" />
	<script src="https://js.api.here.com/v3/3.1/mapsjs-core.js"type="text/javascript" charset="utf-8"></script>
	<script src="https://js.api.here.com/v3/3.1/mapsjs-service.js"type="text/javascript" charset="utf-8"></script>
	</head>
	  
	<body style='margin: 0'>
	<div style="width: 100%; height: 100%" id="mapContainer"></div>
	
	<script>	
	      // Initialize the platform object:
	      var platform = new H.service.Platform({
	        'apikey': 'YOUR API KEY'
	      });
		  
		   const lat = 22.719568;
		   const long = 75.857727;
		
		// Obtain the default map types from the platform object
	      var maptypes = platform.createDefaultLayers();
	
	      // Instantiate (and display) a map object:
	      var map = new H.Map(
	        document.getElementById('mapContainer'),
	        maptypes.vector.normal.map,
	        {
	          zoom: 10,
	          center: { lat: lat, lng: long }  
	        });
			
		var marker = new H.map.Marker({ lat: lat, lng: long });
			
		// Add the marker to the map:
		map.addObject(marker);
			
	</script>
	</body>
	</html>


Running the code
Open the command prompt or terminal and run the Python code. Alternatively, you can also run code in the IDE like Spyder, PyCharm, etc.
 
An IP address will appear, http://127.0.0.1:5000.
Copy this address and paste it in any of the browser application (Chrome, Mozilla, Internet Explorer, Safari, etc.) and you will see a HERE Map with the specified Latitude and Longitude!
 
Step :- Check Whether pip is installed in your system  
Step 2:- Check whether the flask is installed or not and check version of it 



Folder Directory 
 
Folder Directory 


 
Pyserver :-  
