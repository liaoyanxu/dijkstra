# dijkstra

```c
#include<bits/stdc++.h>
using namespace std;
#define int long long
typedef pair<int,int> edge;
vector<edge> g[21000];
int n,m,s,d[21000],vis[21000],t;
signed main(){
    cin>>n>>m;
	int u,v,w;
	for(int i=1;i<=m;i++){
		scanf("%lld %lld %lld",&u,&v,&w);
		g[u].push_back(make_pair(w,v));
		g[v].push_back(make_pair(w,u));
	}
	cin>>s>>t; 
	memset(vis,0,sizeof(vis));
	memset(d,0x3f,sizeof(d));
	priority_queue<edge,vector<edge>,greater<edge> >q;
	d[s]=0;
	q.push(make_pair(0,s));
	while(!q.empty()){
		edge p=q.top();
		q.pop();
		int u=p.second;
		if(vis[u]) continue;
		vis[u]=1;
		for(int i=0;i<g[u].size();i++){
			int v=g[u][i].second,w=g[u][i].first;
			if(!vis[v]&&d[u]+w<d[v]){
				d[v]=d[u]+w;
				q.push(make_pair(d[v],v));
			}
		}
	}
	if(d[t]==4557430888798830399) cout<<-1<<endl ;
	else cout<<d[t]<<endl;
	return 0;
}
```
