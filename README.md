# Knapsackery

An attempted solution to the problem posed by Ampersand Commerce at 2013's Manchester StudentHack. http://ampersandcommerce.com/studenthack13/

## The Problem
Imagine you’re a retailer…
 
You make local deliveries to your customers using a hired fleet of vehicles.

The packages that you despatch are all cubes, but vary in size and weight. The vans that you hire each have a corresponding cost and a maximum weight and cube capacity.

Below this description is a test data set that defines the packages that need to be despatched, these are provided as a JSON array with an ID, weight and cube. A solution should be built that accepts a JSON array of vehicles with values for type, maximum cube, maximum weight and price. Your solution should return a JSON array with each of the vehicles that are required, the IDs of the packages that are to be despatched within each vehicle and a total cost. It can be assumed that an unlimited supply of vans and drivers is available to you.

The solutions should be optimised for the least cost way of despatching all of the provided packages, whilst still remaining within the constraints of each of the vehicles hired.

Hackers will be judged based on the accuracy of the solutions and the speed of the algorithm. Extra credit will given for building the solution as a web service and for any automated testing that is included in the solution.

## Testing
Ensure all dependencies are installed. Node, NPM, make, MongoDB, etc.

At the minute, the different Vans are stored in MongoDB, and the server will use the database in it's calculations.

First, start the database with:

    ~$ (sudo) mongod

and the node server with:

    ~$ npm start

Make sure everything's ok with:

    ~$ make test

To test with the sample Item sets, run:

    ~$ make api-test

Which will print the output of the packing algorithm using the items stored in lib/packages.json.

## Notes

TODO:

Automatically calculate weightings used in item ordering.
- need to know the average ratio of weight:cube and balance it out to order the items
- e.g. if weight = 2*cube, apply 0.33 to weight and 0.67 to cube.

if there's time: 

Possible extensions of models/PackingStrategy.coffee:
1: 

    1) Keep instantiating large vans and adding item at a time
    2) When all items are added to a van, try and minimise the van.