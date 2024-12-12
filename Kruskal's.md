<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Kruskal's Algorithm</title>
</head>
<body>
    <pre>
#include &lt;iostream&gt;

using namespace std;

class d {
public:
    int u;
    int v;
    int w;
};

int find(int arr[50], int u, int v) {
    if (arr[u] == arr[v]) {
        return 1;
    } else {
        return 0;
    }
}

void union_set(int arr[50], int u, int v, int n) {
    int temp = arr[u];
    for (int i = 0; i &lt; n; i++) {
        if (arr[i] == temp) {
            arr[i] = arr[v];
        }
    }
}

void Merge(d B[], int p, d C[], int q, d A[]) {
    int i = 0, j = 0, k = 0;

    while (i &lt; p && j &lt; q) {
        if (B[i].w &lt;= C[j].w) {
            A[k++] = B[i++];
        } else {
            A[k++] = C[j++];
        }
    }
    while (i &lt; p) {
        A[k++] = B[i++];
    }
    while (j &lt; q) {
        A[k++] = C[j++];
    }
}

void MergeSort(d A[], int n) {
    if (n &gt; 1) {
        int mid = n / 2;

        d B[50], C[50];
        for (int i = 0; i &lt; mid; i++) {
            B[i] = A[i];
        }
        for (int i = mid; i &lt; n; i++) {
            C[i - mid] = A[i];
        }

        MergeSort(B, mid);
        MergeSort(C, n - mid);
        Merge(B, mid, C, n - mid, A);
    }
}

int main() {
    int n, e;
    cout &lt;&lt; "Enter the number of vertices and edges: ";
    cin &gt;&gt; n &gt;&gt; e;

    d d1[50];
    cout &lt;&lt; "Enter the edges (u v w):" &lt;&lt; endl;
