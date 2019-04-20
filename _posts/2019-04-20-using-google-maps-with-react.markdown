---
layout: post
title: 'Using Google Maps Autocomplete with React'
date: 2019-04-20 21:45:00 +1000
categories: learning react google maps
---

I start a new job soon, and it's going to be very maps heavy. I haven't done an awful lot with maps & geolocation before so I thought this was a good thing to play with. I decided I wanted to create an app that showed a map to a user (original right?) and also allowed the user to add addresses/locations which would then be listed in the navigation pane on the website and would also show as markers on the map. I've also been learning React, so I wanted to use that as well. I did some searching and came across [this post on medium][medium-post] which suggested using ['google-maps-react'][npm-google-maps-react] so that's what I went with. There's may be other/better libraries/options out there, but this one does what I need. For this, you'll need a Google Maps API Key.

First things first, create your react app. Checkout [Facebook's Github Readme][facebook-github] for info on that.

Install google-maps-react
`npm install --save google-maps-react`

I created a components folder in the 'src' folder, and created a 'MyMap.js' file:
{% highlight javascript %}
/* src/components/MyMap.js */
import React from 'react';
import { Map, GoogleApiWrapper } from 'google-maps-react';

class MyMap extends React.Component {
    loadAutocomplete(mapProps, map) {
        const input = document.getElementById('map_address');
        const dropdown = new window.google.maps.places.Autocomplete(input);
        dropdown.addListener('place_changed', () => {
            const place = dropdown.getPlace();
            new window.google.maps.Marker({
                position: place.geometry.location,
                map: map
            })
        });
    }
    render() {
        return (
            <Map
                google={this.props.google}
                zoom={14}
                onReady={this.loadAutocomplete}
            />
        );
    }
}

export default GoogleApiWrapper({
    apiKey: 'YOUR API KEY HERE',
})(MyMap);
{% endhighlight %}

I stripped out a lot of the stuff that's automatically included in the base react app.
My App.js file:
{% highlight javascript %}
/* src/App.js */
import React, { Component } from 'react';
import MyMap from './components/mymap';

class App extends Component {
    preventEnter = e => {
        if (e.keyCode === 13) {
            e.preventDefault();
        }
    };
    render() {
        return (
            <div className="App">
                <input
                    type="text"
                    name="map_address"
                    id="map_address"
                    onKeyDown={this.preventEnter}/>
                <MyMap />
            </div>
        );
    }
}

export default App;
{% endhighlight %}

And that's it. Pretty simple implementation, but there's lot's of room to improve it from here.

[medium-post]: https://medium.com/@hamza.qaisrani.hq/using-the-google-maps-places-autocomplete-javascript-api-in-a-react-project-5742bab4abc9
[npm-google-maps-react]: https://www.npmjs.com/package/google-maps-react
[facebook-github]: https://github.com/facebook/create-react-app
