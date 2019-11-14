# UFO-server-location

### Rapport on slow pages from america and asia.

# Problem
Some customers have complained about the site being slow from america and asia, the app is having a lot of small request to the server, and which indicate the problem might be latency/ping.

# Problem-statement
The further away(geographicly) the customer is from our server, the higher the latency they experince.

# Hypothesis
There is a correlation between distance from client to server and the latency (responsetime from client to server)

# Experiment
We will try to prove our hypothesis by using the [ping command](https://en.wikipedia.org/wiki/Ping_(networking_utility)) 
We are using this tool [ipgeolocation.io](https://ipgeolocation.io/) to locate a server in USA and a server close t our location
```
Location    IPadr                   pingtime
USA         8.8.8.8 (google dns)    avg. 20.1 ms.
Denmark     46.36.209.7 (dandomain) avg. 13.0 ms    
```

This small experiment seems to back our claim from the hypothosis. (a ping test from our location to somewhere in asia has been omitted)

# Thoughts
The right way to investigate this issue is to monitor latency directly on our usecase, it can be done with new relic browser insight [1], which monitors the time it takes for each request, as well as information from where in the world the request is made. 
This data would be crucial in locating the problem.

The next best thing to do, would be a ping test from europe, to asia and america - to get some initials numbers for the latency, however this data will be misleading, because a ping server in america possibly have a better network connection than a server in america, and the my connection here might be 


| Ping from bph bussiness  | To digital ocean nyc  | DO amstadam | DO singapore |
| ------------- |:-------------|:-------------| -----|
|ping|188|37|356|
|download|37|40|10,5|

And from this data, we can see that the ping over the atlantic ocean is large, and its even greater to asia. It would be possible to get this time way down if the server (a replica) was located closer to the user.



[1] https://newrelic.com/products/browser-monitoring
