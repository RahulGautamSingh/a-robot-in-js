# Description
[link](https://eloquentjavascript.net/07_robot.html)
Robo postman is an automation in the virtual world. It's task is to collect and deliver mails in the virtual world.

Name of Virtual World: Meadowfield Village 
Description of Meadowfield: 
Small village with 11 places to go and 14 roads you can take
Residents: 5 (Alice, Daria, Ernie, Grete, Bob)
Places: 11 (5 resident houses, Marketplace, Post Office, Cabin, Farm, Town Hall, Shop)

```js
const roads = [
  "Alice's House-Bob's House",   "Alice's House-Cabin",
  "Alice's House-Post Office",   "Bob's House-Town Hall",
  "Daria's House-Ernie's House", "Daria's House-Town Hall",
  "Ernie's House-Grete's House", "Grete's House-Farm",
  "Grete's House-Shop",          "Marketplace-Farm",
  "Marketplace-Post Office",     "Marketplace-Shop",
  "Marketplace-Town Hall",       "Shop-Town Hall"
];
```

Now the postman needs to move from place to place through the roads. 
We will think of the roads as a graph, cause it's easier for calculation and better than an array fof strings in terms of readability.
Below is a fn in JS that will convert the roads array into a graph.

```js
function buildGraph(edges) {
  let graph = Object.create(null);
  function addEdge(from, to) {
    if (from in graph) {
      graph[from].push(to);
    } else {
      graph[from] = [to];
    }
  }
  for (let [from, to] of edges.map(r => r.split("-"))) {
    addEdge(from, to);
    addEdge(to, from);
  }
  return graph;
}

const roadGraph = buildGraph(roads);
```

Given array of roads, `buildGraph` creates an objects that stores the places and an array of places connected to it via a road.

# Task



