# Routeboxer
This is a git clone of the googlecode project http://google-maps-utility-library-v3.googlecode.com/svn/trunk/routeboxer/docs/examples.html
The RouteBoxer class generates a set of LatLngBounds objects that are guaranteed to cover every point within a specified distance of a path, such as that generated for a route by the DirectionsService class

## How to use
To use the RouteBoxer class, first load the RouteBoxer.js file into your page:

```html
<script type="text/javascript" src="http://google-maps-utility-library-v3.googlecode.com/svn/trunk/routeboxer/src/RouteBoxer.js"></script>
```

Then create a RouteBoxer object, and pass an array of google.maps.LatLng objects and a distance to the RouteBoxer.box() method. If implementing search along a route the overview_polyline property of a google.maps.DirectionsRoute object contains a suitable array of LatLng objects:

```javascript
var directionService = new google.maps.DirectionsService();
var rboxer = new RouteBoxer();
var distance = 20; // km

directionService.route(request, function(result, status) {
  if (status == google.maps.DirectionsStatus.OK) {

    // Box the overview path of the first route
    var path = result.routes[0].overview_path;
    var boxes = routeBoxer.box(path, distance);

    for (var i = 0; i < boxes.length; i++) {
      var bounds = box[i];
      // Perform search over this bounds
    }
  }
});
```

Original author: Thor Mitchell
