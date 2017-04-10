# ReactiveXHR
Reactive way of handling HTTP Request/Response


## Basic Use of APIs should be like this

#### Register API Keys
```javascript
ReactiveXHR.register({
  "update_profile" : "/api/user/profile/edit",
  "update_trip" : "/api/trip/{code}/update"
})
```

#### In Module 1 : Profile Edit Module
```javascript
var rx = new ReactiveXHR();

rx.send("update_profile",{ fname : "Lalit"}).done(function(){
  // Not mandatory, but do when done.
});
```

#### In Module 2 : Header Module
```javascript
var rx = new ReactiveXHR();

rx.on("update_profile",function(req, resp){
  // update name in header module
});
```

#### In Module 3 : Sidebar Module
```javascript
var rx = new ReactiveXHR();

rx.on("update_profile",function(req, resp){
 // update sidebar module
});
```


## More possible options

```javascript
rx.send("update_trip",{ rider_name : "Ramo"}, { "code" : "002" });

//Possible ways to subscribe
rx.on("update_trip",function(req, resp, meta){
 // do something
});
rx.on("update_trip/code=002",function(req, resp, meta){
 // do something
});
rx.on("update_trip?rider_name=Ramo",function(req, resp, meta){
 // do something
});
rx.on("update_trip#rider_name=Ramo",function(req, resp, meta){
 // assuming response is if format { rider_name : "Ramo"}
});

```





