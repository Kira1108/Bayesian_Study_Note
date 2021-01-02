# Bayesian Serious - Part V Overarching Problem example
## 1. 网络就是这么个网络
![](Bayesian%20Serious%20-%20Part%20V%20Overarching%20Problem%20example/CB4FA20A-E1FC-4B86-B343-8FDCA31C2949%202.png)

## 问题1: Cancelation ⟂ Customer Type ? - NO [D-separation]
![](Bayesian%20Serious%20-%20Part%20V%20Overarching%20Problem%20example/9ED2A20D-6BC8-4029-8CC5-DC44B92A0E18%202.png)


## 问题2: Cancelation ⟂ Customer Type ｜ Usage ? - YES [D-separation]
![](Bayesian%20Serious%20-%20Part%20V%20Overarching%20Problem%20example/08418565-B200-4C6A-AC06-E790798EEFEA%202.png)

## 问题3: P(Cancel = Yes | region = North)?             

**Step 1: 反手一个贝叶斯**              
P(cancel = yes | region = North)            
= P(region = north | cancel = yes) * P(cancel = yes) / P(region = north)            
= P(region = north, cancel = yes) /  P(region = north)              


**Step 2: Enumeration**              
T = Customer Type          
R = Region           
N = Number of products           
U = Usage             
P = Price increase           
C = Customer cancel         

P(region = north, cancel = yes) =             
**[sum over t, n, u, p ]** P(T = t) * P(R = north|T = t) * P(N = n|T = t, R = north) *             
P(U = u |T = t, R = north, N = n) *  P( P=p| T = t, R = north, N = n,U = u) *              
P(C = yes|T = t, R = NORTH, N = N, U = u, P = p)                    

**Step 3: Elimination**               
1. Customer Type he Region 是absolute independent的。             
![](Bayesian%20Serious%20-%20Part%20V%20Overarching%20Problem%20example/71EA00B4-DE42-48DE-B9B3-6778E46E20B0%202.png)
P(R = north | T = t) = P(R = north)               
P(T = t) P(R =north) 都是直接可以从表里面查出来的             

2. P(N = n|T = t, R = north)            
这是Number of product 这个表里面可以直接查出来的           

3. P(U = u |T = t, R = north, N = n) = P(U = u | N = n)               
当我given T - type, R - region的时候， N(number of products)和 T, R 是无关的               
然后这个就能从第三个conditional probability表里面查出来了。          
![](Bayesian%20Serious%20-%20Part%20V%20Overarching%20Problem%20example/1F855FEC-17D0-462B-806F-B403B5DAE107%202.png)

4. P( P=p| T = t, R = north, N = n,U = u) = P(P = p | U = u)              
给定U的时候， P和 T, R, N 是无关的， 然后这个也可以从conditional probability 表里面读出来了。         
![](Bayesian%20Serious%20-%20Part%20V%20Overarching%20Problem%20example/07985B5A-0CA5-4BEF-8761-F6F9E7C0E20B%202.png)


5. P(C = yes|T = T, R = NORTH, N = N, U = u, P = p) = P(C= yes | U = u, P = p)            
给定P，U的时候， C和T, R, N无关, 这个就可以从最后一个conditional proabbility表里面求出来了       
![](Bayesian%20Serious%20-%20Part%20V%20Overarching%20Problem%20example/A40C3DE5-48C6-45C6-8916-C5FD991189D3%202.png)

**Step 4 Rewrite formula**                 

P(region = north, cancel = yes) =              
**[sum over t, n, u, p ]**            
P(T = t) *                       -> 从Type拿                    
P(R = north) *                   -> 从Region拿                   
P(N = n|T = t, R = north) *      -> 从Number products拿          
P(U = u |N = n) *                -> 从Usage拿                           
P(C = yes, U = u, P = p)          -> 从cancel拿   

这个地方要注意的是，最后是一个joint probability， 因为P受到U的影响，最后一起影响C        

**没错，你的人生就是这么痛苦**
我们沿着贝叶斯网络改写一下连加号
**[sum over T=t, R=north]** P(T = t, R  =north)                         
**[sum over N=n]** P(N = n|T = t, R = north)            
**[Sum over U=u]** P(U = u |N = n)                               
**[Sum part U=u, P=p]** P(C = yes, U = u, P = p)     
最后一步要算U, P的conditional table，在乘一下UP-C的那个table就好了         


**Step 5: 好了，现在可以带入公式了 Walk down the network**                  
![](Bayesian%20Serious%20-%20Part%20V%20Overarching%20Problem%20example/85D2124B-9712-4DD6-998D-9935B7726F47%202.png)

1) 首先计算不同类型和区域的概率               
![](Bayesian%20Serious%20-%20Part%20V%20Overarching%20Problem%20example/94FEC20B-0600-489B-B88C-93F04251DBF6%202.png)    

实际上我们就需要这两行 (因为Region给定了north)
![](Bayesian%20Serious%20-%20Part%20V%20Overarching%20Problem%20example/41C692F5-01F5-4FC4-AF0B-944B10630AC5%202.png)    


2) 然后计算不同产品数量的概率            
![](Bayesian%20Serious%20-%20Part%20V%20Overarching%20Problem%20example/0193B5C7-159D-4DB4-AFCB-7756B76D9961%202.png)             


3) 然后计算不同用量（Usage）的概率                  
![](Bayesian%20Serious%20-%20Part%20V%20Overarching%20Problem%20example/82FF925E-1551-48AD-8DB6-C952F37B9095.png)      
  


4) 然后计算不同 Price increase的概率  [其实不用算这一步的]          
![](Bayesian%20Serious%20-%20Part%20V%20Overarching%20Problem%20example/A3F0CBA0-EA83-4FC0-8223-CB921511F536.png)



5) 计算一个price increase和Usage的conditional table               
![](Bayesian%20Serious%20-%20Part%20V%20Overarching%20Problem%20example/D38178B4-A479-4CDA-B3D9-18F703D41283.png)




6) 计算结果                   
![](Bayesian%20Serious%20-%20Part%20V%20Overarching%20Problem%20example/CC4A3423-4FEA-4D8E-8AD3-99B69A2D9F5E.png)

= 0.1224025                               

**没错， 人生就是这么痛苦**           

7) P(R = north) = P(R = north, cancel=yes) + P(R = North, cancel = no)


## 问题 4: P(Type = Hospital|Cancel = Yes)

