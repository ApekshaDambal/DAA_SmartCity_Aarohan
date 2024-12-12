---
layout: default
title: Graph Algorithms
---

# Graph Algorithms

## 1. Kruskal's Algorithm

Kruskal's Algorithm is a method for finding the Minimum Spanning Tree (MST) of a connected, undirected graph.

```cpp```
#include <iostream>
#include <algorithm>
using namespace std;

class Edge {
public:
    int u, v, w;
};

int find(int parent[], int i) {
    if (parent[i] == -1)
        return i;
    return find(parent, parent[i]);
}

void union_set(int parent[], int x, int y) {
    int xset = find(parent, x);
    int yset = find(parent, y);
    parent[xset] = yset;
}

bool compare(Edge a, Edge b) {
    return a.w < b.w;
}

void kruskal(Edge edges[], int n, int e) {
    sort(edges, edges + e, compare);
    int parent[n];
    fill_n(parent, n, -1);

    cout << "Minimum Spanning Tree (MST):" << endl;
    for (int i = 0; i < e; i++) {
        int u = edges[i].u;
        int v = edges[i].v;

        if (find(parent, u) != find(parent, v)) {
            cout << u << " -- " << v << " == " << edges[i].w << endl;
            union_set(parent, u, v);
        }
    }
}

int main() {
    int n, e;
    cout << "Enter the number of vertices and edges: ";
    cin >> n >> e;

    Edge edges[e];
    cout << "Enter the edges (u v w):" << endl;
    for (int i = 0; i < e; i++) {
        cin >> edges[i].u >> edges[i].v >> edges[i].w;
    }

    kruskal(edges, n, e);
    return 0;
}
