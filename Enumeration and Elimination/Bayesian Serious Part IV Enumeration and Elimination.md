# Bayesian Serious Part IV Enumeration and Elimination

## 1. Important Probabilities recap

![](Bayesian%20Serious%20Part%20IV%20Enumeration%20and%20Elimination/01059B2D-73D2-4F31-83C5-241495A8546F.png)

1. 第一个特别简单，就是一个简单的贝叶斯公式。            
2. 第二个看看，其实吧，就是一个marginal probability，这个marginal可以在另外一个变量的所有可能上做一次joint probability的相加.              
假设C只有两个可能的值， C 和 notC， 那么P(A) = P(A,C) +  P(A,⌐C)                                                    
如果你非要在这个marginal上加一个conditional的B，就变成 P(A｜B) = P(A,C｜B) +  P(A,⌐C｜B)               
如果C的取值有很多个的情况下，你可以用一个连加号来代表所有可能的C。                                   
你还可以在这个公式上面在加一个其他的变量，一起来算出来一个joint的A的marginal，不过是连加号中可能的（变量）值多了几个而已。                       
3. 第三个吧，上面的，其实就是一个简简单单的条件概率， 把连加号里面的joint probability拆成了prior *  likelihood了，如此简单          
第三个，下面的，就是一个极其简单的多变量Joint Probability的计算。                    

::人生不在于小聪明-能够推导出这些公式，在于拿到一个概率，能用合适的形式写出来一个能够求解的公式。::      


## 2. Calculate Posterior Probabilities in Bayes network    
 
![](Bayesian%20Serious%20Part%20IV%20Enumeration%20and%20Elimination/31D56F8A-7DA2-4FE8-AD55-18817841362C.png)


## 3. Enumeration

**第一个问题的步骤：**
![](Bayesian%20Serious%20Part%20IV%20Enumeration%20and%20Elimination/D5E036AD-9C26-41A6-B146-FEFDB74D868B.png)


当我们要计算给定约翰和凯特不见面的条件下，约翰出去跑步的概率有多大。我们先反手一个贝叶斯。           
为什么要反手一个贝叶斯呢，你通常可能会想，找出所有俩人不见面的天，然后你去计算一下，有100%多少的时候John跑步了，不就完了么。           
我感觉啊              
1. Your data can never be ‘enough’           
2. 有的posterior我们不能直接从dataset中观测到的          
当然上面两点我都不太确定是不是这样， 为了利用这个网络，我们暂且跟着作者的思路继续往下走下去。                 
![](Bayesian%20Serious%20Part%20IV%20Enumeration%20and%20Elimination/32778A52-8012-4460-BA56-7B1CC70EAF0C.png)

### 3.1 我们先算Joint Probability

这儿就用到了上面的公式了，当我们算margina的时候，我们可以用很多的其他变量的joint来joint出来，我们最终想要的Marginal。  
![](Bayesian%20Serious%20Part%20IV%20Enumeration%20and%20Elimination/A9EAD396-9C2F-47AB-A57B-EC1278A72C66.png)
这儿凯特和天气是需要遍历的，所以会出现这么一个丑丑的连加号
T - K - J - M 这个顺序写，是因为业务就是这么个业务，你写出来的东西最好是有逻辑意义的东西。   

最后你把 Joint写成 Conditional *  Prior这种形式就可以了
![](Bayesian%20Serious%20Part%20IV%20Enumeration%20and%20Elimination/A0DB3F9B-6B2B-4131-BBF0-F5761ED1AD65.png)
 
**结合一点D-separation的东西**     
- [ ] 把Kate干掉               
除此之外，如果我们用D-separation的方法，我们还知道，在给定天气的情况下，john和Kate是相对无关的。           
由于没有joint child，我们直接干掉temperature， john 和 kate之间就没有连接了，所以这俩是相对无关的。     
P(John | Kate, Temperature = high) = P(John| Temperature = high)               
![](Bayesian%20Serious%20Part%20IV%20Enumeration%20and%20Elimination/5192BD03-E164-4F03-8EB2-B9C61810376B.png)
所以在上面的公式中 P(J=yes | K=k, T=t) = P(J=yes | T=t), 我们把Kate干掉了                

- [ ] 把temperature干掉    
并且，我们还知道, Meet和Temperature，在给定John 跑步和Kate跑步的情况下，是相对无关的。     
P(Temperature = high | John = yes, Kate=yes, Meet = no) = P(Temperature = high | John=yes, Kate=yes)     
![](Bayesian%20Serious%20Part%20IV%20Enumeration%20and%20Elimination/0DF6E959-464E-4FBE-9157-5ECCAF721817.png)
P(M = no | K=k, J=yes, T=t) = P(M=no | K=k, J=yes), 我们把Temperature干掉了        


然后这个公式就简化成    
![](Bayesian%20Serious%20Part%20IV%20Enumeration%20and%20Elimination/A0DB3F9B-6B2B-4131-BBF0-F5761ED1AD65%202.png)

P(T) P(K|T) P(J|T) P(M | K,J),这些东西，都是可以从conditional probability中求出来的。    


### 3.2 然后我们算Marginal P(M=no)
其实这个Marginal的时候，是要Joint一切的，即使你分解成两个joint，还是要继续往上走bayes network的    
![](Bayesian%20Serious%20Part%20IV%20Enumeration%20and%20Elimination/E07811D2-EBC0-46C5-9196-4C057602C096.png)

第一项我们在3.1中已经求解过了， 第二项你一看样子， 和第一项长相基本差不多，你可以用同样的方法求出来    

### 3.3 结果
把3.1和3.2的东西都带入，自然就能求解这个问题了    

然而这一些都要一顿向上走过去的。    
当我们有很多的变量的这时候，这个连加号需要处理的东西，是指数级增长的，这个时候我们就需要想办法。   


## 4. Elimination     
前面我们计算一个 Joint Probability的时候，我们去遍历了每个中间变量之间所有可能组合，现在我们把这些东西从中间都提出来。                  
左边的一个连加号和K相关，右边的一个连加号和T相关。                         
从我们的Bayes network中可以知道，这个影响顺序的是 T -> JK ->M             
然后从这个conditional tables我们也可看出，T 和John和Kate都是有一张现成的conditional probability table的，我们可以直接去查好了。          
然后呢K和J影响M的时候，也是有一个conditional probability table的，我们可以把分开求这些乱七八糟的东西。             
这样就省的遍历所有变量之间所有可能的组合了。              
![](Bayesian%20Serious%20Part%20IV%20Enumeration%20and%20Elimination/71AD677E-F418-489F-A6ED-7B905815413E.png)


然后我们看看后面的这一项             
![](Bayesian%20Serious%20Part%20IV%20Enumeration%20and%20Elimination/26E5F051-71F3-454B-869F-CEF00873FF13.png)
这一项其实就是一个joint probability P(T = t, K = k, J = j) 我们sum over T变量所有的t的时候，这个公式就可以改写成     
P(J=yes, K = k)这样了. 我们不知不觉把T从这个公式里面干掉了。                 
但是T其实是没有完全干掉的， 我们想要知道P(J,K)这个joint probability的时候，还是要和T去搞事情的，但不用在这个公式里面去搞。                       

**这样，我们就能顺着贝叶斯网络一步一步往下走，求解这些个乱七八糟的东西了**                            


## 5. Elimination Continued

首先我们把这个表在copy一遍。        
![](Bayesian%20Serious%20Part%20IV%20Enumeration%20and%20Elimination/344F84D8-DDC8-4102-A2C9-D5BD63EC7942.png)

然后我们其实要做两步就好了               
1. P(J=yes, K = k)              
2. 后面一切 (其实就是知道了J和K的跑步情况，带入到JK跑步meet的conditional probability表)             
		
**Step 1**                  
这是一张Joint probability的大表格            
John   Kate  probability            
yes    yes   0.395             
yes    no    0.225           
 
其中，第一个概率             
P(T = low) P( John=yes | T = low)* P(Kate = yes| T = low) + P(T = high) P( John=yes | T = high)* P(Kate = yes| T = high)           
= 0.4 * 0.5 * 0.4 + 0.6 * 0.7 * 0.75 = 0.395            
其中其中, 由于给定天气的情况下，John he Kate是相对无关的, 所以           
P(Kate = yes |T=low, John = yes) = P(Kate = yes | T = low)           

其中， 第二个概率                    
P(T = low) P( John=yes | T = low)* P(Kate = no| T = low) + P(T = high) P( John=yes | T = high)* P(Kate = no| T = high)                
= 0.4 * 0.5 * 0.6 + 0.6 * 0.7 * 0.25 = 0.225             

**Step 2**
P(M = no | Kate = yes, John = yes) * P(John = yes, Kate = yes) +             
P(M = no | Kate = no, John = yes) * P(John = yes, Kate = no)           

=0.5 * 0.395 + 0.225 * 1 = 0.4225                     



**这样算概率，简直是太痛苦了， 在工程中直接应用这种理论的东西，宛如智障**

        