cordova-indoors
===============

Cordova/Phonegap Plugin for indoo.rs


EXAMPLE USAGE: 

```javascript
IndoorNav.init('APIKEY', 'BUILDINGID');

$(window).unload(function() {
  IndoorNav.destruct();
});


IndoorNav = {
		
	init: function(apikey, building) {
		IndoorNav.indoors = new indoors(apikey, building);
		IndoorNav.indoors.onmessage = function(e) {
   			console.log('MESSAGE: ' + e.data.indoorsEvent + ' | DATA: ' + e.data.indoorsData) ; //TODO
    	};
    	IndoorNav.indoors.onsuccess = function(e) {
   			console.log('SUCCESS: ' + e.data.indoorsEvent + ' | DATA: ' + e.data.indoorsData); //TODO
    	};
    	IndoorNav.indoors.onerror = function(e) {
   			console.log('ERROR: ' + e.data.indoorsEvent + ' | DATA: ' + e.data.indoorsData) ; //TODO
    	};
	},
	
	destruct: function() {
		if(typeof IndoorNav.indoors != 'undefined') {
			IndoorNav.indoors.destruct();
		}
	}
};
```
