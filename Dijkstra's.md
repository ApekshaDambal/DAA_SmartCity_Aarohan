
<pre>
#include &lt;iostream&gt;
#include &lt;climits&gt;

using namespace std;

class Dijkstra
{
public:
    int cost[100][100];
    int v;
    int dist[10]; 
    int path[10]; 
    int visited[10]; 

    void read_cost(int cost[100][100], int v);
    void initiate(int arr[10], int n);
    void shortest_path(int src);
    void print_path(int src);
};

void Dijkstra::read_cost(int cost[100][100], int v)
{
    cout &lt;&lt; "Enter the cost matrix:\n";
    for (int i = 0; i &lt; v; i++)
    {
        for (int j = 0; j &lt; v; j++)
        {
            cin &gt;&gt; cost[i][j];
            if (cost[i][j] == 0 && i != j)
            {
                cost[i][j] = INT_MAX; 
            }
        }
    }
}

void Dijkstra::initiate(int arr[10], int n)
{
    for (int i = 0; i &lt; n; i++)
    {
        arr[i] = 0;
    }
}

void Dijkstra::shortest_path(int src)
{
    for (int i = 0; i &lt; v; i++)
    {
        dist[i] = INT_MAX;
        visited[i] = 0;
        path[i] = -1;
    }
    dist[src] = 0; 
    for (int count = 0; count &lt; v - 1; count++)
    {
        int min_dist = INT_MAX, u;

        for (int i = 0; i &lt; v; i++)
        {
            if (!visited[i] && dist[i] &lt; min_dist)
            {
                min_dist = dist[i];
                u = i;
            }
        }

        visited[u] = 1; 

        for (int i = 0; i &lt; v; i++)
        {
            if (!visited[i] && cost[u][i] != INT_MAX && dist[u] != INT_MAX && dist[u] + cost[u][i] &lt; dist[i])
            {
                dist[i] = dist[u] + cost[u][i];
                path[i] = u; // Update the path
            }
        }
    }
}

void Dijkstra::print_path(int src)
{
    cout &lt;&lt; "Vertex\tDistance from Source\tPath" &lt;&lt; endl;
    for (int i = 0; i &lt; v; i++)
    {
        cout &lt;&lt; i &lt;&lt; "\t" &lt;&lt; dist[i] &lt;&lt; "\t\t";

        int temp = i;
        while (temp != -1 && temp != src)
        {
            cout &lt;&lt; temp &lt;&lt; " &lt;- ";
            temp = path[temp];
        }
        if (i != src)
            cout &lt;&lt; src;

        cout &lt;&lt; endl;
    }
}

int main()
{
    Dijkstra d;
    int src;

    cout &lt;&lt; "Enter the number of vertices: ";
    cin &gt;&gt; d.v;

    d.read_cost(d.cost, d.v);

    cout &lt;&lt; "Enter the source vertex: ";
    cin &gt;&gt; src;

    d.shortest_path(src);
    d.print_path(src);

    return 0;
}
</pre>
