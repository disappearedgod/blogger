---
title: LeetCode|Graph| 133 Clone Graph

date: 2020-07-14 12:12:57
categories: 
- LeetCode
tag: ["LeetCode","Graph"]
---
---
# [题目](https://leetcode.com/problems/clone-graph/)
Given a reference of a node in a connected undirected graph.

Return a deep copy (clone) of the graph.

Each node in the graph contains a val (int) and a list (List[Node]) of its neighbors.

> class Node {
>     public int val;
>     public List<Node> neighbors;
> }
 

Test case format:

For simplicity sake, each node's value is the same as the node's index (1-indexed). For example, the first node with val = 1, the second node with val = 2, and so on. The graph is represented in the test case using an adjacency list.

Adjacency list is a collection of unordered lists used to represent a finite graph. Each list describes the set of neighbors of a node in the graph.

The given node will always be the first node with val = 1. You must return the copy of the given node as a reference to the cloned graph.

 

Example 1:
![](Cypress_Field_Rendering.png )


> Input: adjList = [[2,4],[1,3],[2,4],[1,3]]
> Output: [[2,4],[1,3],[2,4],[1,3]]
> Explanation: There are 4 nodes in the graph.
> 1st node (val = 1)'s neighbors are 2nd node (val = 2) and 4th node (val = 4).
> 2nd node (val = 2)'s neighbors are 1st node (val = 1) and 3rd node (val = 3).
> 3rd node (val = 3)'s neighbors are 2nd node (val = 2) and 4th node (val = 4).
> 4th node (val = 4)'s neighbors are 1st node (val = 1) and 3rd node (val = 3).

Example 2:
![](graph.png )


> Input: adjList = [[]]
> Output: [[]]
> Explanation: Note that the input contains one empty list. The graph consists of only one node with val = 1 and it does not have any neighbors.

Example 3:

> Input: adjList = []
> Output: []
> Explanation: This an empty graph, it does not have any nodes.

Example 4:
![](graph-1.png )

> Input: adjList = [[2],[1]]
> Output: [[2],[1]]
 

Constraints:

1 <= Node.val <= 100
Node.val is unique for each node.
Number of Nodes will not exceed 100.
There is no repeated edges and no self-loops in the graph.
The Graph is connected and all nodes can be visited starting from the given node.

# solve

## DFS

```javascript
/**
 * // Definition for a Node.
 * function Node(val, neighbors) {
 *    this.val = val === undefined ? 0 : val;
 *    this.neighbors = neighbors === undefined ? [] : neighbors;
 * };
 */

/**
 * @param {Node} node
 * @return {Node}
 */

// DFS
var cloneGraph = function(node) {
    if(node === null){
        return node;
    }
    
    map = new Map();
    const clone = root =>{
        if( !map.has(root.val) ){
            map.set(root.val, new Node(root.val) );
            map.get(root.val).neighbors = root.neighbors.map(clone);
        }
        return map.get(root.val);
    }
    return clone(node);
};

```


## 迭代模版


```javascript
var cloneGraph = function(node) {
    if(!node){
        return null;
    }
    const queue = [node], visited = new Map();

    visited.set(node, new Node(node.val))
    while(queue.length > 0 ){
        const curr = queue.pop()
        curr.neighbors.forEach(neigbor =>{
            if(!visited.has(neigbor)){
                visited.set(neigbor, new Node(neigbor.val))
                queue.unshift(neigbor)
            }
            
            const cloned = visited.get(curr)
            const cloneN = visited.get(neigbor)
            cloned.neighbors.push(cloneN)
        });
    }
    
    return visited.get(node);

}
```