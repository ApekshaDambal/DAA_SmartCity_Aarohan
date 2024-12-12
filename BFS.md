<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>BFS Traversal</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f9;
            padding: 20px;
        }
        pre {
            background-color: #e8e8f0;
            border: 1px solid #ccc;
            padding: 15px;
            border-radius: 5px;
            overflow-x: auto;
        }
    </style>
</head>
<body>
    <h1>BFS Traversal Code</h1>
    <pre>
#include &lt;iostream&gt;
using namespace std;

void bfs(int m[10][10], int v, int source) {
    int queue[20];
    int front = 0, rear = 0, u, i;
    int visited[10];

    for (i = 0; i &lt; v; i++)
        visited[i] = 0;

    queue[rear] = source;
    visited[source] = 1;

    cout &lt;&lt; "The BFS Traversal is... \n";

    while (front &lt;= rear) {
        u = queue[front];
        cout &lt;&lt; u &lt;&lt; "\t";
        front++;

        for (i = 0; i &lt; v; i++) {
            if (m[u][i] == 1 &amp;&amp; visited[i] == 0) {
                visited[i] = 1;
                rear++;
                queue[rear] = i;
            }
        }
    }
}

int main() {
    int v = 5;
    int m[10][10] = {{0,1,1,0,0}, {1,0,0,1,1},
        {1,0,0,0,1}, {0,1,0,0,0}, {0,1,1,0,0}};

    int source;
    cout &lt;&lt; "Enter the source vertex: ";
    cin &gt;&gt; source;

    bfs(m, v, source);

    return 0;
}
    </pre>
</body>
</html>
