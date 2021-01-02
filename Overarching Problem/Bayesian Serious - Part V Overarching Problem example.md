# Bayesian Serious - Part V Overarching Problem example
## 1. 网络就是这么个网络
![](Bayesian%20Serious%20-%20Part%20V%20Overarching%20Problem%20example/CB4FA20A-E1FC-4B86-B343-8FDCA31C2949.png)

## 问题1: Cancelation ⟂ Customer Type ? - NO [D-separation]
![](Bayesian%20Serious%20-%20Part%20V%20Overarching%20Problem%20example/9ED2A20D-6BC8-4029-8CC5-DC44B92A0E18.png)


## 问题2: Cancelation ⟂ Customer Type ｜ Usage ? - YES [D-separation]
![](Bayesian%20Serious%20-%20Part%20V%20Overarching%20Problem%20example/08418565-B200-4C6A-AC06-E790798EEFEA.png)

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
![](Bayesian%20Serious%20-%20Part%20V%20Overarching%20Problem%20example/71EA00B4-DE42-48DE-B9B3-6778E46E20B0.png)
P(R = north | T = t) = P(R = north)               
P(T = t) P(R =north) 都是直接可以从表里面查出来的             

2. P(N = n|T = t, R = north)            
这是Number of product 这个表里面可以直接查出来的           

3. P(U = u |T = t, R = north, N = n) = P(U = u | N = n)               
当我given T - type, R - region的时候， N(number of products)和 T, R 是无关的               
然后这个就能从第三个conditional probability表里面查出来了。          
![](Bayesian%20Serious%20-%20Part%20V%20Overarching%20Problem%20example/1F855FEC-17D0-462B-806F-B403B5DAE107.png)

4. P( P=p| T = t, R = north, N = n,U = u) = P(P = p | U = u)              
给定U的时候， P和 T, R, N 是无关的， 然后这个也可以从conditional probability 表里面读出来了。         
![](Bayesian%20Serious%20-%20Part%20V%20Overarching%20Problem%20example/07985B5A-0CA5-4BEF-8761-F6F9E7C0E20B.png)


5. P(C = yes|T = T, R = NORTH, N = N, U = u, P = p) = P(C= yes | U = u, P = p)            
给定P，U的时候， C和T, R, N无关, 这个就可以从最后一个conditional proabbility表里面求出来了       
![](Bayesian%20Serious%20-%20Part%20V%20Overarching%20Problem%20example/A40C3DE5-48C6-45C6-8916-C5FD991189D3.png)

**Step 4 Rewrite formula**                 

P(region = north, cancel = yes) =              
**[sum over t, n, u, p ]**            
P(T = t) *                       -> 从Type拿                    
P(R = north) *                   -> 从Region拿                   
P(N = n|T = t, R = north) *      -> 从Number products拿          
P(U = u |N = n) *                -> 从Usage拿                
P(P=p|U = u) *                  -> 从Price increase拿              
P(C = yes|U = u, P = p)          -> 从cancel拿            

**没错，你的人生就是这么痛苦**
我们沿着贝叶斯网络改写一下连加号
**[sum over T=t, R=north]** P(T = t, R  =north)                         
**[sum over N=n]** P(N = n|T = t, R = north)            
**[Sum over U=u]** P(U = u |N = n)          
**[Sum over P=p]** P(P=p|U=u)                        
**[Sum part U=u, P=p]** P(C = yes|U = u, P = p)              


**Step 5: 好了，现在可以带入公式了 Walk down the network**                  
![](Bayesian%20Serious%20-%20Part%20V%20Overarching%20Problem%20example/85D2124B-9712-4DD6-998D-9935B7726F47.png)

1) 首先计算不同类型和区域的概率               
![](Bayesian%20Serious%20-%20Part%20V%20Overarching%20Problem%20example/94FEC20B-0600-489B-B88C-93F04251DBF6.png)    

实际上我们就需要这两行 (因为Region给定了north)
![](Bayesian%20Serious%20-%20Part%20V%20Overarching%20Problem%20example/41C692F5-01F5-4FC4-AF0B-944B10630AC5.png)    


2) 然后计算不同产品数量的概率            
![](Bayesian%20Serious%20-%20Part%20V%20Overarching%20Problem%20example/0193B5C7-159D-4DB4-AFCB-7756B76D9961.png)             


3) 然后计算不同用量（Usage）的概率                  
![](Bayesian%20Serious%20-%20Part%20V%20Overarching%20Problem%20example/9B6588C0-1885-4303-9D9D-39A8F7C47608.png)    


4) 然后计算不同 Price increase的概率             
![](Bayesian%20Serious%20-%20Part%20V%20Overarching%20Problem%20example/68EC4289-D642-4917-B860-2129869376E4.png)   


5) 计算一个price increase和Usage的conditional table             
![](Bayesian%20Serious%20-%20Part%20V%20Overarching%20Problem%20example/C1676C2B-34A9-4257-8DF2-2166DAA1F3AA.png) 



6) 计算结果                   
![](Bayesian%20Serious%20-%20Part%20V%20Overarching%20Problem%20example/A16F96FA-F0B2-4076-80F0-E9688B74E4C5.png)
= 0.0188683234038166                      

### 没错， 人生就是这么痛苦
