# Bayesian Serious

## 1. Basic Probability [Thats too simple]
Probability must be between 0 and 1
Probability +  Complementary Probability = 1
Probability of all possible events must add up to 1


## 2. Contingency Table [Very important Thing]
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







#statistics