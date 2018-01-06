# elevator-challenge

> Elevator Programming Challenge

You should plan to spend 2 hours on this challenge, committing to a github repo approximately every 15 minutes.

You're designing the software that simulates elevators in a building.
Design a set of objects that will manage elevator movement and interaction between the
elevators. The elevator simulation should support these features:

1. Initialize the elevator simulation with the desired number of elevators, and the desired
number of floors. Assume ground/min of 1.
2. Each elevator will report as is moves from floor to floor.
3. Each elevator will report when it opens or closes its doors.
4. An elevator cannot proceed above the top floor.
5. An elevator cannot proceed below the ground floor (assume 1 as the min)
6. An elevator request can be made at any floor, to go to any other floor.
7. When an elevator request is made, the unoccupied elevator closest to it will answer the
call, unless an occupied elevator is moving and will pass that floor on its way. The
exception is that if an unoccupied elevator is already stopped at that floor, then it will
always have the highest priority answering that call.
8. The elevator should keep track of how many trips it has made, and how many floors it
has passed. The elevator should go into maintenance mode after 100 trips, and stop
functioning until serviced, therefore not be available for elevator calls.

## Build Setup

``` bash
# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run build

# build for production and view the bundle analyzer report
npm run build --report
```

For a detailed explanation on how things work, check out the [guide](http://vuejs-templates.github.io/webpack/) and [docs for vue-loader](http://vuejs.github.io/vue-loader).
