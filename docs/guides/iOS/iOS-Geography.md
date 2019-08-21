## Geography on iOS

NStack supports a list of geographical features. 

You can get and store 
* list of countries, continents, languages and timezones of the world; 
* get timezone for coordinate (lat, lng); 
*  get geographical information based on the requestee's ip address. 

For example:

~~~~swift
NStack.sharedInstance.timezone(lat: 12.0, lng: 55.0) { (timezone, error) in
    if let timezone = timezone {
        print("(12.0,55.0) is in timezone \(timezone.name)")
    }
}
~~~~

Read more about **Geography** in [*Features/Geography*](../../features/geographic.html)