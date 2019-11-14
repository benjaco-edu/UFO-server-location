# UFO-server-location

Rapport on slow pages from america and asia.

Some customers have complained about the site being slow from america and asia, the app is having a lot of small request to the server, and which indicate the problem might be latency/ping.

The right way to investigate this issue is to monitor latency directly on our usecase, it can be done with new relic browser insight [1], which monitors the time it takes for each request, as well as information from where in the world the request is made. 
This data would be crucial in locating the problem.

The next best thing to do, would be a ping test from europe, to asia and america - to get some initials numbers for the latency, however this data will be misleading, because a ping server in america possibly have a better network connection than a server in america, and the my connection here might be 


| Ping from bph bussiness  | To digital ocean nyc  | DO amstadam | DO singapore |
| ------------- |:-------------|:-------------| -----|
|ping|188|37|356|
|download|37|40|10,5|

And from this data, we can see that the ping over the atlantic ocean is large, and its even greater to asia. It would be possible to get this time way down if the server (a replica) was located closer to the user.



[1] https://newrelic.com/products/browser-monitoring
