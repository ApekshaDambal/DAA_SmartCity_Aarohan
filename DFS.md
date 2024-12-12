<html>
<head>
    <title>DFS Traversal Code</title>
</head>
<body>
    <h1>DFS Traversal Code</h1>
    <pre>
#include &lt;iostream&gt;
using namespace std;

int v = 5;
int m[10][10] = {{0,1,1,0,0}, {1,0,0,1,1},
        {1,0,0,0,1}, {0,1,0,0,0}, {0,1,1,0,0}};
int visited[10];

void dfs(int m[10][10], int v, int source) {
    visited[source] = 1;
    for (int i = 0; i < v; i++) {
        if (m[source][i] == 1 && visited[i] == 0) {
            cout &lt;&lt; i &lt;&lt; "\t";
            dfs(m, v, i);
        }
    }
}

int main() {
    int source;
    for (int i = 0; i < v; i++)
        visited[i] = 0;

    cout &lt;&lt; "Enter the source vertex: ";
    cin &gt;&gt; source;

    cout &lt;&lt; "The DFS Traversal is... \n";
    cout &lt;&lt; source &lt;&lt; "\t";
    dfs(m, v, source);

    return 0;
}
    </pre>
</body>
</html>
