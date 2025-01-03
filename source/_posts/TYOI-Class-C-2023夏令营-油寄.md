---
title: TYOI Class C 2023夏令营 油寄
date: 2023-08-26 09:57:00
categories:
- 记录
---

## Week1

### Day1

$\color{white}{\texttt{生病在家躺着，别提了。}}$

### Day两

下午来学校，做了一会早上的比赛题然后就去洛谷找题做了。

晚上边咳嗽边跑两圈，~~感觉要死了~~。

### Day3

今天学强连通分量，本蒟蒻觉得自己不会，就拿老师的模版代码自己加了点注释，在 oiclass 发了一个[帖](http://oiclass.com/d/puji/discuss/64d2f5223f87425ba26c2525#1691722265305)问大家是不是这样，不过没人回~~只有人膜~~。做了两题之后觉得挺简单的，~~不就是 dfs 和两个 if 嘛~~，那我理解得应该没问题。

<!--more-->

```cpp
void tarjan(int u){
	dfn[u]=low[u]=++index;//编号
	s.push(u);
	inStack[u]=true;
	for(int i=0;i<G[u].size();++i){
		int v=G[u][i];//new
		if(dfn[v]==-1){//未访问
			tarjan(v);//dfs
			low[u]=min(low[u],low[v]);//回溯
		}else{//已访问
			if(inStack[v]){//绕了一圈又回来了（强连通）
				low[u]=min(low[u],dfn[v]);
			}
		}
	}
	if(dfn[u]==low[u]){//无后向边
		c++;//强连通分量的编号
		int v;
		do{
			v=s.top();
			s.pop();			//把自己的子树pop
			scc[v]=c;
			inStack[v]=false;
		}while(u!=v);			//把自己pop
	}
}

```


还是咳个不停，所以晚上回家。

### Day4

今天的比赛第一题就是个贪心红题，T两 本来老师想考我们高精度 sqrt ，结果数据只有 $10^{20}$ 被我们用 unsigned long long 和 long double 卡过，T3 判断条件写错，只要数据里有 1 3 2 这类子序列就会挂，还好数据淼只少了十分。T4 后来看好像一个容斥加数学，我怎么可能会，于是就前面的数据用暴力，后面 rand() 50pts。赛后发现删掉 rand() 那部分代码 70pts 当场裂开。$\color{white}\texttt{三周后的我：哇只挂了 两十 分我好强啊。}$

下午改完题发现了[这道题](https://www.luogu.com.cn/problem/T364320)，玩了好一会，又去随机跳题加了几道题到任务计划里~~但可是一道没做~~。

终于能在学校住宿了，我的床太软了，仰着的时候屁股陷下去很不舒服。

晚上聊了一堆好玩的东西，UTC15:30 才睡。

### Day5

割点与桥，加强版Tarjan，没什么的就不说了。

晚上打了[比赛](https://www.luogu.com.cn/contest/121028)，开幕雷击：

![](https://cdn.luogu.com.cn/upload/image_hosting/umw7mfqp.png)

P的，CF只有在你得到正Rating时才会有这个牌子。

不过[麻辣兔头](https://www.luogu.com.cn/problem/B3815)尝起来很不错。

晚上熄灯后趁他们聊天时背下了《般若波罗蜜多心经》

```
观自在菩萨
行深般若波罗蜜多时
照见五蕴皆空
度一切苦厄
舍利子
色不异空
空不异色
色即是空
空即是色
受想行识
亦复如是
舍利子
是诸法空相
不生不灭
不垢不净
不增不减
是故空中无色
无受想行识
无眼耳鼻舌身意
无色声香味触法
无眼界
乃至无意识界
无无明
亦无无明尽
乃至无老死
亦无老死尽
无苦集灭道
无智亦无得
以无所得故
菩提萨埵
依般若波罗蜜多故
心无罣碍
无罣碍故
无有恐怖
远离颠倒梦想
究竟涅磐
三世诸佛
依般若波罗蜜多故
得阿耨多罗三藐三菩提
故知般若波罗蜜多
是大神咒
是大明咒
是无上咒
是无等等咒
能除一切苦
真实不虚
故说般若波罗蜜多咒
即说咒曰:
揭谛揭谛
波罗揭谛
波罗僧揭谛
菩提萨婆诃
揭谛揭谛
波罗揭谛
波罗僧揭谛
菩提萨婆诃
揭谛揭谛
波罗揭谛
波罗僧揭谛
菩提萨婆诃
```

### Day6

早上的比赛大挂分榜倒一，T3 理解错题意寄，T2 化简为繁寄。

下午[打比赛](https://www.luogu.com.cn/contest/123900#description)，太多速通高手，我被打爆了。

回到家爆肝MC两个小时半，本来要骑驴去沙漠探险的，结果玩着玩着就去玩了飞行模组，找了半个小时不知道怎么加油，怒砸电脑。

## Week两

### Day1

橙名啦！

早上写了一个[0+1 problem](https://www.luogu.com.cn/problem/T366848)。

并查集太简单了。就是一个图论版小递归。

```
for(int i=1;i<=n;++i)
		fa[i]=i;

int find(int n){
	if(fa[n]==n)
		return n;
	return fa[n]=find(fa[n]);
}
```

我似乎晚上什么也没干。

### Day两

何致远奆佬给我们出了一个非常简单的比赛，估计蓝蓝紫紫橙，最后6坤分加道签到题总算推出数学公式。~~学长真良心~~。

### Day3

T3 DP 初始值搞错，T两 算错复杂度。

T3 赛时：
```cpp
#include<iostream>
#define int long long
using namespace std;
int x,y,z;
int a[102],b[102],c[102],f[102][102][102];
signed main(){
	cin>>x>>y>>z;
	for(int i=x;i>=1;--i){
		cin>>a[i];
	}
	for(int i=y;i>=1;--i){
		cin>>b[i];
	}
	for(int i=z;i>=1;--i){
		cin>>c[i];
	}

	for(int i=1;i<=x;++i){
		for(int j=1;j<=y;++j){
			for(int k=1;k<=z;++k){
				f[i][j][k]=max(f[i][j][k],f[i][j][k-1]+(i+j+k)*c[k]);
				f[i][j][k]=max(f[i][j][k],f[i][j-1][k]+(i+j+k)*b[k]);
				f[i][j][k]=max(f[i][j][k],f[i-1][j][k]+(i+j+k)*a[k]);
			}
		}
	}
	cout<<f[x][y][z];
}
```

正解：

```cpp
#include<cmath>
#include<stack>
#include<queue>
#include<cstdio>
#include<string>
#include<vector>
#include<cstring>
#include<iostream>
#include<algorithm>
#define PI pair<int,int>
#define MP(u,v) make_pair((u),(v))
#define R register
#define U unsigned
#define IL inline
//#define int long long
using namespace std;
const int INF=0x3f3f3f3f;
const int mod=1e9+7;
const int N=1e2+10;
const int M=1e3;
int x,y,z;
int n;
int f[N][N][N][12],a[N][13];
int main(){
	scanf("%d%d%d",&x,&y,&z);
	n=x+y+z;
	for(int i=1;i<=x;i++)
		scanf("%d",&a[i][1]);
	for(int i=1;i<=y;i++)
		scanf("%d",&a[i][2]);
	for(int i=1;i<=z;i++)
		scanf("%d",&a[i][3]);
	for(int i=1;i<=x/2;i++)
		swap(a[i][1],a[x-i+1][1]);
	for(int i=1;i<=y/2;i++)
		swap(a[i][2],a[y-i+1][2]);
	for(int i=1;i<=z/2;i++)
		swap(a[i][3],a[z-i+1][3]);
	f[1][0][0][0]=a[1][1],f[0][1][0][0]=a[1][2],f[0][0][1][0]=a[1][3];
	for(int i=2;i<=n;i++){
		for(int j=0;j<=min(i,x);j++){
			for(int k=0;k<=min(i-j,y);k++){
				int l=i-j-k;
				if(j>0)
					f[j][k][l][1]=max(f[j][k][l][1],f[j-1][k][l][0]+a[j][1]*i);
				if(k>0)
					f[j][k][l][1]=max(f[j][k][l][1],f[j][k-1][l][0]+a[k][2]*i);
				if(l>0)
					f[j][k][l][1]=max(f[j][k][l][1],f[j][k][l-1][0]+a[l][3]*i);
				f[j][k][l][0]=f[j][k][l][1];
			}
		}
	}
	printf("%d\n",f[x][y][z][1]);
	return 0;
}
```

呜呜呜。

### Day4

基础的最小生成树，就是贪心套并查集，我觉得我半年前都听得懂。

```cpp
#include <stdio.h>
#include <stdlib.h>
#define N 9   // 图中边的数量
#define P 6   // 图中顶点的数量
//构建表示边的结构体
struct edge {
    //一条边有 2 个顶点
    int initial;
    int end;
    //边的权值
    int weight;
};

//qsort排序函数中使用，使edges结构体中的边按照权值大小升序排序
int cmp(const void* a, const void* b) {
    return  ((struct edge*)a)->weight - ((struct edge*)b)->weight;
}
//克鲁斯卡尔算法寻找最小生成树，edges 存储用户输入的图的各个边，minTree 用于记录组成最小生成树的各个边
void kruskal_MinTree(struct edge edges[], struct edge minTree[]) {
    int i, initial, end, elem, k;
    //每个顶点配置一个标记值
    int assists[P];
    int num = 0;
    //初始状态下，每个顶点的标记都不相同
    for (i = 0; i < P; i++) {
        assists[i] = i;
    }
    //根据权值，对所有边进行升序排序
    qsort(edges, N, sizeof(edges[0]), cmp);
    //遍历所有的边
    for (i = 0; i < N; i++) {
        //找到当前边的两个顶点在 assists 数组中的位置下标
        initial = edges[i].initial - 1;
        end = edges[i].end - 1;
        //如果顶点位置存在且顶点的标记不同，说明不在一个集合中，不会产生回路
        if (assists[initial] != assists[end]) {
            //记录该边，作为最小生成树的组成部分
            minTree[num] = edges[i];
            //计数+1
            num++;
            elem = assists[end];
            //将新加入生成树的顶点标记全部改为一样的
            for (k = 0; k < P; k++) {
                if (assists[k] == elem) {
                    assists[k] = assists[initial];
                }
            }
            //如果选择的边的数量和顶点数相差1，证明最小生成树已经形成，退出循环
            if (num == P - 1) {
                break;
            }
        }
    }
}

void display(struct edge minTree[]) {
    int cost = 0, i;
    printf("最小生成树为:\n");
    for (i = 0; i < P - 1; i++) {
        printf("%d-%d  权值：%d\n", minTree[i].initial, minTree[i].end, minTree[i].weight);
        cost += minTree[i].weight;
    }
    printf("总权值为：%d", cost);
}

int main() {
    int i;
    struct edge edges[N], minTree[P - 1];
    for (i = 0; i < N; i++) {
        scanf("%d %d %d", &edges[i].initial, &edges[i].end, &edges[i].weight);
    }
    kruskal_MinTree(edges, minTree);
    display(minTree);
    return 0;
}
```

Prim 有点难还不会。

```cpp
#define MAXN 1000
#define INF 1<<30
int closest[MAXN],lowcost[MAXN],m;//m为节点的个数
int G[MAXN][MAXN];//邻接矩阵
int prim()
{
    for(int i=0;i<m;i++)
    {
        lowcost[i] = INF;
    }
    for(int i=0;i<m;i++)
    {
        closest[i] = 0;
    }
    closest[0] = -1;//加入第一个点，-1表示该点在集合U中，否则在集合V中
    int num = 0,ans = 0,e = 0;//e为最新加入集合的点
    while (num < m-1)//加入m-1条边
    {
        int micost = INF,miedge = -1;
        for(int i=0;i<m;i++)
        if(closest[i] != -1)
        {
            int temp = G[e][i];
            if(temp < lowcost[i])
            {
                lowcost[i] = temp;
                closest[i] = e;
            }
            if(lowcost[i] < micost)
            micost = lowcost[miedge=i];
        }
        ans += micost;
        closest[e = miedge] = -1;
        num++;
    }
    return ans;
}
```

狼人杀不知道盗宝偷的技能能持续到白天，痛失赢。

### Day5

下午晚上爆刷16道黄绿题。

自学以前没学会的 Dijkstra 和 SPFA。

### Day6

第一题想不出来，上个厕所瞬间AC。

## Week3

### Day1

最小生成树进阶。还行，至少比Prim简单。

爆切15题，写出第一篇题解。

### Day2

看到[新加坡国宝游戏公司](https://gbc.ljcoier.repl.co/gp),

```
温馨提示（免责声明）：股票有风险，投资须谨慎，此股票为虚假股票，不要当真
股票走向规则，保证随机，可买可卖。
想成功先发疯、不顾一切向钱冲。拼一次富三代、拼命才能不失败。今天睡地板，明天当老板。小孩子才分对错，大人只看输赢。等伤害到自己的利益了又能拿出道德标准拿起对错。只有你们想不到的，没有我们做不了的！！！！
```

### Day3

下午新初生离开，我们可高兴了，我的“九点两十五分”和“I also”出名了。

我都不知道我 T1 怎么AC的。

### Day4

这个星期踢足球真开心，就是脚好痛啊。

### Day5

中午终于把[P1462](https://www.luogu.com.cn/problem/P1462)做完了，提交了5页评测记录。

T3 long long `%d`梅开二度挂100。

下午踢全场，好大啊。

### Day6

写这篇东西写到崩溃，到Week3已经乱写了。

---

感觉：上课和比赛总是神游，状态很不好，想好也好不了。但自由做题时就感觉良好。同学们都大大滴好，天天去204玩杀和牌可高兴了。
