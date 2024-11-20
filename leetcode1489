#include <stdio.h>
#include <stdlib.h>

typedef struct {
    int weight;
    int u;
    int v;
    int index;
} Edge;

int compareEdges(const void *a, const void *b) {
    return ((Edge *)a)->weight - ((Edge *)b)->weight;
}

int find(int *parent, int x) {
    if (parent[x] != x) {
        parent[x] = find(parent, parent[x]);
    }
    return parent[x];
}

void unionSets(int *parent, int *rank, int x, int y) {
    int rootX = find(parent, x);
    int rootY = find(parent, y);
    if (rootX != rootY) {
        if (rank[rootX] > rank[rootY]) {
            parent[rootY] = rootX;
        } else if (rank[rootX] < rank[rootY]) {
            parent[rootX] = rootY;
        } else {
            parent[rootY] = rootX;
            rank[rootX]++;
        }
    }
}

int kruskal(int n, Edge *edges, int edgeCount, int skipEdge, int includeEdge) {
    int *parent = (int *)malloc(n * sizeof(int));
    int *rank = (int *)malloc(n * sizeof(int));
    for (int i = 0; i < n; i++) {
        parent[i] = i;
        rank[i] = 0;
    }
    
    int mstWeight = 0;
    int edgeUsed = 0;
    
    if (includeEdge != -1) {
        Edge edge = edges[includeEdge];
        unionSets(parent, rank, edge.u, edge.v);
        mstWeight += edge.weight;
        edgeUsed++;
    }
    
    for (int i = 0; i < edgeCount; i++) {
        if (i == skipEdge) continue;
        Edge edge = edges[i];
        if (find(parent, edge.u) != find(parent, edge.v)) {
            unionSets(parent, rank, edge.u, edge.v);
            mstWeight += edge.weight;
            edgeUsed++;
        }
    }
    
    free(parent);
    free(rank);
    
    return edgeUsed == n - 1 ? mstWeight : INT_MAX;
}

int** findCriticalAndPseudoCriticalEdges(int n, int** edges, int edgesSize, int* edgesColSize, int* returnSize, int** returnColumnSizes) {
    Edge *edgeList = (Edge *)malloc(edgesSize * sizeof(Edge));
    for (int i = 0; i < edgesSize; i++) {
        edgeList[i].weight = edges[i][2];
        edgeList[i].u = edges[i][0];
        edgeList[i].v = edges[i][1];
        edgeList[i].index = i;
    }
    
    qsort(edgeList, edgesSize, sizeof(Edge), compareEdges);
    
    int originalMSTWeight = kruskal(n, edgeList, edgesSize, -1, -1);
    
    int *critical = (int *)malloc(edgesSize * sizeof(int));
    int *pseudoCritical = (int *)malloc(edgesSize * sizeof(int));
    int criticalCount = 0;
    int pseudoCriticalCount = 0;
    
    for (int i = 0; i < edgesSize; i++) {
        int weightWithoutEdge = kruskal(n, edgeList, edgesSize, i, -1);
        if (weightWithoutEdge > originalMSTWeight) {
            critical[criticalCount++] = edgeList[i].index;
        } else {
            int weightWithEdge = kruskal(n, edgeList, edgesSize, -1, i);
            if (weightWithEdge == originalMSTWeight) {
                pseudoCritical[pseudoCriticalCount++] = edgeList[i].index;
            }
        }
    }
    
    *returnSize = 2;
    *returnColumnSizes = (int *)malloc(2 * sizeof(int));
    (*returnColumnSizes)[0] = criticalCount;
    (*returnColumnSizes)[1] = pseudoCriticalCount;
    
    int **result = (int **)malloc(2 * sizeof(int *));
    result[0] = (int *)malloc(criticalCount * sizeof(int));
    result[1] = (int *)malloc(pseudoCriticalCount * sizeof(int));
    
    for (int i = 0; i < criticalCount; i++) {
        result[0][i] = critical[i];
    }
    for (int i = 0; i < pseudoCriticalCount; i++) {
        result[1][i] = pseudoCritical[i];
    }
    
    free(edgeList);
    free(critical);
    free(pseudoCritical);
    
    return result;
}
