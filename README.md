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
    		try {
    			console.log('MESSAGE: ' + e.data.indoorsEvent + ' | DATA: ' + e.data.indoorsData) ; //TODO
    		}
    		catch (e) {}
    	};
    	IndoorNav.indoors.onsuccess = function(e) {
    		try {
    			console.log('SUCCESS: ' + e.data.indoorsEvent + ' | DATA: ' + e.data.indoorsData); //TODO
    			if(e.data.indoorsEvent == 'connected') {
    				IndoorNav.indoors.setUsername('MyName'); //TODO
    			} 
    		}
    		catch (e) {}
    	};
    	IndoorNav.indoors.onerror = function(e) {
    		try {
    			console.log('ERROR: ' + e.data.indoorsEvent + ' | DATA: ' + e.data.indoorsData) ; //TODO
    		}
    		catch (e) {}
    	};
	},
	
	destruct: function() {
		if(typeof IndoorNav.indoors != 'undefined') {
			IndoorNav.indoors.destruct();
		}
	}
};
```
