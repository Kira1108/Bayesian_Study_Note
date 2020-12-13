# Bayesian Serious

## 1. Basic Probability [That‘s too simple] 
Probability must be between 0 and 1             
Probability +  Complementary Probability = 1               
Probability of all possible events must add up to 1                 


## 2. Bayes theorem & Contingency Table [Very important Thing]
![](Bayesian%20Serious/90BABBC0-E12D-40FD-9450-99F00C645BBB.png)

### First thing to know about contingency table
Two variables in the above table            
1 - Temperature y - axis             
2 - Weather x - axis           
Draw each variable on one axis, with probability of all possible events.               

x轴相加 = 1， y轴相加 = 1               

### Second thing to know about contingency table
![](Bayesian%20Serious/38809B51-741F-4F84-82A1-5A927F4944B7.png)


Sum of the first row = right most value of second row           
Sum of the second row = right most value of second row            
Sum of the first column = down most value of first column           
Sum …..                                                 

::Cells in the middle are Joint probablities::         
::中间红色区域的概率都是Joint Probability::            
     
**Why sum of cells equal boundary cells**         
P(Sunny) = P(Sunny & High) +  P(Sunny & Low)               
P(Cloudy) = P(Cloudy & High) +  P(Cloudy & Low)            
P(Rainy) = P(Rainy & High) +  P(Rainy & Low)
P(High) = P(High & Sunny) +  P(High & Cloudy) + P(High & Rainy)           
P(Low) = P(Low & Sunny) + P(Low & Cloudy) +  P(Low & Rainy)            

### Third Thing to know about contingency table - Conditional probability

Your description:               
One day you wake up in the morning, you feel hot [Temperature is high], what is the probability the weather being sunny.    
More formal:         
What is the probability of the weather being sunny, given temperature is high.        
Mathematical:          
P(W = Sunny | T = high) = P(W = Sunny & T = high) / P(T = high) =  .25 / .7          

你也可以想象成，总共有100天， 其中有70天温度高， 30天温度低           
温度高，且 晴天的的天数是25天，已知现在温度比较高，那是晴天的概率就是 25 / 70 [因为你已经知道今天温度高了]            

### Fourth Thing to know about contingency table 

Sum of probabilities of all possible events over one variable          
Conditioned on the same event of another variable            
The value needs to be 1.            

这个其实就是上面的上面的上面那个东西的变种          
**P(Sunny | high) + P(Cloudy | high) +  P(Rainy | high) = 1**               
P(sunny & high) +  P(cloudy & high) +  P(rainy & high) = P(high)           
P(sunny & high) / P(high) +  P(cloudy & high) / P(high) +  P(rainy & high) / P(high) = 1         

条件概率的条件都一样，把所有可能的event加起来，是 = 1的      
你必须condition on 一样的东西 （高温）           
你必须加起来所有的可能（天气无非晴天，阴天， 雨天）             

由于我们已经知道了conditional probability  和 marginal probability了           
P(Sunny | high) + P(Cloudy | high) +  P(Rainy | high) = 0.25 / 0.7 + 0.28 / 0.7 + 0.17/0.7 = 0.7          


### Fifth thing to know about contingency table
P(sunny | high) == P(sunny) ? that’s not true, not always true.          

If P(sunny |  high) = P(sunny) -> Sunny and temperature high are independent          
           
P(W | T) = P(W) for any combinations of values W -> (Sunny, Cloudy, Rainy), T -> (High,Low)          
-> Weather(W) and Temperature(T) are independent.         

事件的相互独立和变量的相互独立            


## Fill a contingency table
Suppose 1% of people are infected with flu                                   
If you have the flu, you are tested positive with 95% probability                 
If you are not infected, you are tested positive with 10 probability               

**Convert to mathematical expression**
P(flu) = 1%
P(positive | flu) = 95%
P(positive | ~flu) = 10%

The mathematical expression is sufficient to populate a  contingency table
![](Bayesian%20Serious/D2D70C74-4EAE-4F45-8A1F-11584C6EC99E.png)

P(pos & flu) = P(flu) * P(pos|flu) = 0.01 * 0.95 [convert conditional to joint]          
P(pos & ~flu) = P(~flu) * P(pos|~flu) = 0.99 * 0.1 [convert conditional to joint]           
P(pos) = P(pos & flu) + P(pos & ~flu) = 0.01 * 0.95 + 0.99 * 0.1 [column sum]          
P(flu) = P(neg & flu) + P(pos & flu) [row sum]          
P(neg & flu) = P(flu) - P(pos & flu) = 0.01 - 0.01 % 0.95          
P(~flu) = P(neg & ~flu) + P(pos & ~flu) [row sum]              
P(neg & ~flu) = P(~flu) - P(pos & ~flu) = 0.99 - 0.99 * 0.1   

这时候我们把 P(flu) 叫做prior probability     
            

## 4. Wrap up [知道这些东西，你就可以填表了]
1. P(A | B) = P(A & B) / P(B)                
2. P(A1|B) + P(A2|B) + P(A3|B) + ….. +P(An|B) = P(B)            
3. P(B1|A) + P(B2|A) + P(B3|A) + ….. +P(Bn|A) = P(A)           
第二条和第三条相当于：           
	行之和等于最右边的行总计。                   
	列之和等于最下面的列总计            
4. 变量A可能的事件为 A1, A2, A3…..           
P(A1) + P(~A1) = 1               
P(A1) + … + P(An) = 1                           



## OverArching problem 

**Variables:**
Customer Type: Hospital, Doctor’s office
Number of products: 1, >=2   

**Question:**
Given a customer bought 1 product, what is the probability that the customer is a hospital customer. 

**Given:**    
Prior probabilities:      
	P(Hospital) = 0.25,      
	P(Doctor Office) = 1 - P(Hospital) = 0.75   
   
Conditional probabilities:(Sum of probability over all events condition on 1 event of other variables = 1 ) 

这个地方，不是contingency table 里面的Joint probability, 而是likelihood              
	P(Prod=1 |Hospital)   = 0.9          
	P(Prod>=2 | Hospital) =  0.1        

	P(Prod = 1 | Doctor Office) = 0.8         
	P(Prod >=2 | Doctor Office) = 0.2           

 
P(Hospital | Prod = 1) = P(Hospital) * P(Prod = 1 |Hospital) /  P(Prod = 1)             
= 0.25 * 0.9 / P(Prod = 1)                   

P(Prod = 1) = P(Prod = 1 | Hospital) * P(Hospital) +  P(Doctor Office) * P(Prod = 1|Doctor Office)                 
0.25 *  0.9 + 0.75 *  0.8 = 0.825                         

P(Hospital | Prod = 1) = 0.25 * 0.9 / 0.825 = 0.272727     

这个例子的不同之处在于，我们事先知道的Likelihood，要构造出一个contingency table， 我们需要先计算一下 Joint Probability， 然后才能填表。         

![](Bayesian%20Serious/9C0BC7E8-28A6-473B-8D5C-201BF6653338.png)
         

## Monty hall problem
![](Bayesian%20Serious/93327E5C-CC4E-4CF8-8AD6-02EAC135140E.png)

1. 这里重要的一个人把问题分解成表格的形式                     
2. 另外就是每一个单元格开始的时候，知道的是likelihood，所以要计算一下Joint              






      







#statistics