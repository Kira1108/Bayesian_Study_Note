# Bayesian Serious - Part III D-separation

1. Draw the ancestral graph. Construct the “ancestral graph” of **all variables mentioned** in the probability expression. 
This is a reduced version of the original net, 
Consisting only of the **variables mentioned** and **all of their ancestors** (parents, parents’ parents, etc.)

2. For each pair of variables with a common child, draw an undirected edge (line) between them. 
(If a variable has more than two parents, draw lines between every pair of parents.)

3. “Disorient” the graph by replacing the directed edges (arrows) with undirected edges (lines).

4. Delete the givens and their edges. 
If the independence question had any given variables, erase those variables from the graph and erase all of their connections, too. Note that “given variables” as used here refers to the question “Are A and B conditionally independent, given D and F?”, not the equation “P(A|BDF) =? P(A|DF)”, and thus does not include B. 

5. Read the answer off the graph.
 If the variables are disconnected in this graph, they are guaranteed to be independent. 
 If the variables are connected in this graph, they are not guaranteed to be independent.* Note that “are connected” means “have a path between them,” so if we have a path X-Y-Z, X and Z are considered to be connected, even if there’s no edge between them. 
 If one or both of the variables are missing (because they were givens, and were therefore deleted), they are independent.



Give a bayesian net
![](Bayesian%20Serious%20-%20Part%20III%20D-separation/75322622-308F-4B64-A459-2CDC43B12C20.png)


## 在 DF一定时， AB是不是相对无关
![](Bayesian%20Serious%20-%20Part%20III%20D-separation/598FD22D-9E0B-423F-9DDF-D136935D3A9C.png)

1. 找爸爸和爸爸的爸爸们， ABDF出现了，AB没有爸爸，D有C， F有D，C有AB - （ABCDF）
2. 把座位联合子节点的父亲们用无向边连接， ABDF都是独生子女，只有C有AB为爸爸们，所以把AB连接在一起
3. 把所有的有向边转换成无向边
4. 把作为条件 P(|…)的变量从这个图中删除
5. 看到A和B还是连接的，所以他们不一定是相对无关的。


## AB是不是绝对无关
![](Bayesian%20Serious%20-%20Part%20III%20D-separation/38586B2E-7C89-4801-88B5-65C63C9DBD06.png)

1. 找到爸爸们，AB都是最上层的爸爸，没有爸爸了
2. 没有共同的儿子
3. 没有边
4. 没有given变量
5. 不连接 - AB是绝对无关的。


## 给定C的时候，AB是不是相对独立的

![](Bayesian%20Serious%20-%20Part%20III%20D-separation/56826057-2AB1-4E3A-B12F-73EB1B0AFCE5.png)

1. ABC，C有爸爸，AB {A, B, C}
2. C是一个有好多爸爸的儿子，连接AB
3. 无向化
4. 删除given的C
5. AB依然相连， 所以AB在给定C的时候不一定是相对无关的。



## 给定C的时候， D和E是不是相对无关的
![](Bayesian%20Serious%20-%20Part%20III%20D-separation/1B8E4617-118C-4DEA-98EC-5CBF3EC57A2B.png)
1. CDE是所有出现的变量，D有C这个爸爸， E有C这个爸爸， C有AB这俩爸爸 （ABCDE）
2. 无向边连接C的爸爸们
3. 无向化
4. 去掉givenC
5. DE不连接 - 相对独立的


## DE是不是绝对无关的
![](Bayesian%20Serious%20-%20Part%20III%20D-separation/555ED7E0-1469-4C02-883A-FDB5E9ACB6BA.png)
1. DE -> C -> AB (ABCDE)
2. C - (A - B)
3. 无向化
4. 没有given
5. DE通过C连接，他们不一定绝对无关。



## 给定AB的时候，DE是不是先对无关的
![](Bayesian%20Serious%20-%20Part%20III%20D-separation/D9D27599-7658-4490-8C20-81408ABF7F83.png)
1. (ABCDE)
2. 连接爸爸AB
3. 无向化
4. 删除given AB
5. DE连接， 不一定相对无关哟

## E & G 是否和D在给定C的条件下 相对独立
1. D和E在给定C的情况下是否相对独立， 且
2. D和G在给定C的情况下是否相对独立
![](Bayesian%20Serious%20-%20Part%20III%20D-separation/F9319F98-D85B-4603-880D-F2B4B29DF309.png)


一个一个算，最后算一个且，就好了





#statistics