---
marp: true
theme: gaia
_class: lead
#backgroundImage: 
---

# Interconnectedness and systemic risk network of Chinese financial institutions: A LASSO-CoVaR approach

Xi et.al.  Physica A

汇报 苏锦华

---

## 主要观点

- 金融系统风险传播: 2015-2016年中国股市崩盘
- 视角：从网络的角度研究系统性风险
- 方法: 用LASSO来估计CoVaR，以构建金融机构系统性尾部风险网络,网络拓扑分析、高维分位数回归
- 数据：2010-2017年中国金融机构的互联数据
- 实证结果:
    - 在估计单个机构的CoVaR时，机构间的互联性不可忽视
    - 拓扑分析表明，系统级互联性在系统处于困境时达到峰值，尤其是在股市崩盘前后
    - 根据系统性风险贡献对机构排序，发现在四个阶段排序发生变化

---

## 背景

**机构间的风险溢出效应**:2007-2009年全球金融危机使人们认识到，金融机构的相互关联性可能是系统性风险的最重要来源之一，甚至整个金融市场都可能因单个企业破产而不稳定，威胁到整个金融系统。对企业特定风险的准确评估应该考虑其他机构的潜在风险溢出效应。

**大而不倒的底层逻辑**:我们应该更多地关注那些“关联性太强而不能倒”或“系统性太强而不能倒”的机构.。

**中国市场与宏观信息**:市场不够有效,价格并不能完全反映宏观信息。现有的实证结果表明，引入宏观经济信息能够提高中国股市系统性风险度量的准确性。

---

## 问题提出

**在风险传染的视角下，从传染网络的角度研究系统性风险与条件风险**

![](%E4%BC%A0%E6%92%AD%E7%BD%91%E7%BB%9C.png)

---

## 主要研究流程

在2010年1月至2017年12月，50家上市金融机构(商业银行、券商、保险公司和其他公司)。

1. **网络构建**：估计单个机构的条件风险（CoVaR）,以宏观状态、企业特征、其他风险关联机构影响作为条件，其他风险关联机构通过高维分位数回归进行变量选择，使用LASSO自动选择每个机构CoVaR估计中的重要相关者,以此，构建系统性风险网络。
2. **网络分析**:从系统级和扇区级的角度分析了动态网络拓扑特征，如总网络互联性（TS）、部门内输入强度（SI）和部门内输出强度（SO）。

---

## 主要研究流程 cont.

3. **风险预测**:使用滞后的宏观状态变量和所有风险相关机构的VAR估计系统性风险贝塔。
4. **风险排名**:根据系统性风险在金融危机四个阶段的贡献对机构进行排名,根据结果进行相应分析。

![h:300](%E6%8B%93%E6%89%91%E5%88%86%E6%9E%90.png)  ![h:300](%E5%9B%9B%E9%98%B6%E6%AE%B5%E5%8F%98%E5%8C%96.png) 


---

## 相关工作

- Adrian和Brunnermeier[1]以及Acerbi和Tasche[8]专注于风险传染或溢出效应，而我们专注于其他机构的影响。
- 通过利用金融机构之间的所有联系，Wang等人[9]构建了一个网络模型，以研究中国金融机构的互联性和系统重要性。本文使用LASSO将不显著的关系减少到零，并得到一个更简洁的模型。
- 至于构建与其他机构的互联关系，Hautsch等人[2]和Fang等人[10]考虑了他们的尾部风险溢出，这是在估计企业特定VaR时通过损失超标捕获的，而我们将其他机构的VaR视为估计CoVaR的潜在回归器。

---

## 主要贡献

- 将系统性风险和网络互联性统一起来，分别提供了单个机构系统性风险和系统级系统性风险的自然度量
- 结合两阶段分位数回归和LASSO方法来发展LASSO-CoVaR方法,构建了从网络的角度研究系统性风险的简洁网络
- 从金融机构之间的一对一连接到所有金融机构之间的多对一连接的角度来审查相互关联性
- 从单个机构和整个系统的角度衡量系统性风险,以2015-2016年中国股市崩盘期间进行实证分析,得出了风险传播的部分实际规律

---

## 方法:网络构建

1. 系统性风险与条件风险

$$
\operatorname{Pr}\left(L_{t}^{j} \geq \operatorname{CoVaR}_{1-\tau, t}^{j | i} \mid L_{t}^{i}=\operatorname{VaR}_{1-\tau, t}^{i}\right)=1-\tau
$$

$$
\begin{aligned}
L_{t}^{i} &=\beta_{0}^{i}+\beta_{M}^{i} M_{t-1}+\varepsilon_{t}^{i} \\
L_{t}^{j} &=\beta_{0}^{j \mid i}+\beta_{M}^{j \mid i} M_{t-1}+\beta_{L}^{j \mid i} L_{t}^{i}+\varepsilon_{t}^{j \mid i}
\end{aligned}
$$

2. LASSO-CoVaR 方法

$$
\widehat{\operatorname{CoVaR}}_{1-\tau, t}^{j||_{t}^{(j)}}=X_{t}^{(j)} \hat{\beta}_{1-\tau}^{j \mid X_{t}^{(j)}}=\hat{\beta}_{1-\tau, 0}^{j||_{t}^{(j)}}+\hat{\beta}_{1-\tau, M}^{j \mid X_{t}^{(j)}} M_{t-1}+\hat{\beta}_{1-\tau, V a R}^{j \mid x_{t}^{(j)}} V a R_{1-\tau, t}^{-j}+\hat{\beta}_{1-\tau, c}^{j||_{t}^{(j)}} c_{t-1}^{j}
$$

---

## 方法:网络构建 cont.

$$
\hat{\beta}_{1-\tau}^{j \mid x_{t}^{(j)}}=\arg \min _{\substack{j \mid x_{t}^{(j)}}} \frac{1}{T} \sum_{t=1}^{T} \rho_{1-\tau}\left(L_{t}^{j}-X_{t}^{(j)} \beta_{1-\tau}^{j \mid X_{t}^{(j)}}\right)+\lambda^{j} \frac{\sqrt{\tau(1-\tau)}}{T} \sum_{i=1, i \neq j}^{N} \hat{\sigma}_{i}\left|\beta_{1-\tau, V a R^{i}}^{j \mid X_{t}^{(j)}}\right|
$$

$$
A_{i, j}= \begin{cases}\left|\hat{\beta}_{1-\tau, V a R_{1-\tau, t}^{j \mid \bar{x}_{t}^{(j)}}}^{\mid{ }^{j i}}\right|, & \text { if } \operatorname{VaR}_{1-\tau, t}^{j \mid i} \text { is selected, i.e., }\left\langle v_{i},\right. \\ 0, & \text { if } V a R_{1-\tau, t}^{j i i} \text { is not selected, i.e. }\end{cases}
$$


---

## 方法:网络分析

![](%E7%BD%91%E7%BB%9C%E4%BA%A4%E4%BA%92%E6%8C%87%E6%A0%87.png)


---

## 方法:系统风险贡献



$$
\begin{aligned}
&L_{t}^{s}=\beta_{0}^{s \mid j}+\beta_{M}^{s \mid j} M_{t-1}+\beta_{\nu j}^{s \mid j} L_{t}^{j}+\varepsilon_{t}^{s \mid j} \\
&\widehat{C o V a R}_{1-\tau, t}^{s \mid j}=\hat{\beta}_{1-\tau, 0}^{s j}+\hat{\beta}_{1-\tau, M}^{s \mid j} M_{t-1}+\hat{\beta}_{1-\tau, V a R^{j}}^{s j j} \widehat{V a R}_{1-\tau, t}^{j}
\end{aligned}
$$

$$
\widehat{C o V a R}_{1-\tau, t}^{s \mid j}=X_{t}^{(j)^{\prime}} \hat{\beta}_{1-\tau}^{s \mid j}=\hat{\beta}_{1-\tau, 0}^{s j j}+\hat{\beta}_{1-\tau, M}^{s \mid j} M_{t-1}+\hat{\beta}_{1-\tau, V a R^{-j \mid R}}^{s \mid j} V a R_{1-\tau, t}^{-j \mid R}+\hat{\beta}_{1-\tau, V a R^{j}}^{s \mid j} V a R_{1-\tau, t}^{j}
$$

$$
S R C_{1-\tau, t}^{s j} \equiv \hat{\beta}_{1-\tau, V a R^{j}}^{s j} V_{1-\tau, t}^{j}
$$

---

## 实证分析：数据

![h:420](%E6%95%B0%E6%8D%AE%E4%BB%8B%E7%BB%8D.png)


$$
X_{t+s / m}=(1-s / m) X_{t}+(s / m) X_{t+1}, \text { with } s=1,2, \ldots, m
$$


---

## 实证分析：LASSO-CoVaR拟合结果

![bg right:20%](LASSO-CoVaR%E7%B3%BB%E6%95%B0%E7%BB%93%E6%9E%9C%E8%A1%A8.png)

采用LASSO-CoVaR方法测量所有个体机构的CoVaR，τ=0.01、0.05、0.1对应于99%、95%、90%的置信水平。其他分位数水平的结果相似，为了节省空间，仅报告τ=0.01在ABC、SS、CL和SLT的结果。以ABC为例，在估计CoVaR的过程中，LASSO自动选择回归因子MCC、BOB、GGDD、AXTI、GFS和HHI。仅考虑一个机构的传统CoVaR方法不足以理解系统性风险的行为。换句话说，考虑到多个金融机构之间的相互作用，LASSO-CoVaR方法有助于改进CoVaR度量的性能。

---

## 实证分析：回测

对比模型: TENET(Tail-Event driven NETwork risk)

$$
I_{t}^{j}= \begin{cases}1, & \text { if }\left|L_{t}^{j}-V a R_{1-\tau, t}^{j}\right|<\varepsilon \\ 0, & \text { if }\left|L_{t}^{j}-V a R_{1-\tau, t}^{j}\right| \geq \varepsilon\end{cases}
$$

$$
A E=\frac{1}{N} \sum_{j=1}^{N}\left|p_{j}-\tau\right|
$$

![bg right w:600](%E5%9B%9E%E6%B5%8B%E7%BB%93%E6%9E%9C.png)


---

## 实证分析：风险网络

![bg right](%E9%A3%8E%E9%99%A9%E7%BD%91%E7%BB%9C%E5%AE%8C%E6%95%B4.png)

利用机构间的尾部风险联系构建了50家金融机构的系统性风险网络。线厚度显示了影响的大小。盒子大小由机构大小决定。从机构i指向机构j的箭头反映了当机构i遭受损失时，VaRi对VaRj的影响。高度互联的机构有更多的箭头，包括传入和传出箭头。

---

## 实证分析：机构归类

1. **风险发送者**:财务困境会使其他机构陷入极度亏损，但他们受其他机构财务困境的影响较小。监管机构应更加关注这些机构，如BOB和HHI，以防止它们通过网络发送重大系统性风险。
2. **风险承担者**:即对其他机构影响较小但受其影响较大的风险承担者。大多数保险公司都属于这一类，例如XSY、PAI和CPIC。
3. **风险承担者和风险发送者**，他们不仅接受其他机构发送的风险，还将风险分散到其他机构，放大了金融风险的溢出效应。HBS和AXF等机构是系统性风险网络的主要参与者，因此应受到密切监控。

---

## 实证分析:出度与入度

测试了它们的分布是否遵循特定的幂律分布。结果表明，入度和出度均服从幂律分布，α分别为3和1.9627。

![h:300](%E5%87%BA%E5%BA%A6%E5%85%A5%E5%BA%A6.png) ![h:180](%E5%B9%82%E5%BE%8B%E6%A3%80%E9%AA%8C.png)


---

## 实证分析：动态拓扑性质

用S=51周(一年)的滚动窗口方法来构建动态系统性风险网络(2010年至2017年)，TS在2014年年中达到峰值，这与中国股市开始牛市的时间相吻合。

$$
T S_{w}=\sum_{m=1}^{4} S I_{w}^{m}=\sum_{m=1}^{4} S O_{w}^{m}
$$

![bg right:40% h:700](%E5%8A%A8%E6%80%81%E7%BD%91%E7%BB%9C%E5%88%86%E6%9E%90.png)

---

## 实证分析：动态拓扑性质 cont.

- 当时国内资金继续外流。为了留住资金和稳定汇率，股市开始上涨以留住这些资金
- 商业银行当时下调利率，导致货币供应量突然增加。然而，资金并没有流向实体经济，而是流向股市，这导致热钱突然增加
- 当时有很多新股，即大量机构在市场融资和证券借贷。现阶段，TS值迅速上升，表明这些金融机构具有较强的尾部风险溢出效应。这种非理性繁荣形成了金融泡沫，导致中国股市在2015-2016年崩盘。


---

## 实证分析：动态拓扑性质 cont.


- 通过四部门的角度分析网络的互连性,在牛市中，TS的增长主要反映在券商SI的增长上。早期牛市由券商主导。
- 在牛市开始时，保险公司的SI有了显著的增长。随着监管的放松，越来越多的保险公司开始与其他机构签订合同，从事高风险业务。
- 牛市和股市崩盘期间，保险公司的SI保持在相对较高的水平。保险公司作为风险承担者发挥着重要作用
- 当牛市开始时，券商和其他公司的SO会大幅上升。由于对政策的高度敏感性和较高的市场价值，券商的风险高于其他行业。
- 在牛市中，其他公司都存在巨大的市值泡沫。因此，他们的股价下跌将导致股市暴跌

---

## 实证分析：模拟网络ERGM

社会资本理论表明，社会资本越高的用户在社交网络中获得的资源越多。因此使用ERGM通过估计、模拟和测试来检验机构的市值是否会影响系统性风险网络的形成。ERGM指数随机图模型：
$$
P(Y=y \mid \theta)=\frac{\exp \left(\theta^{T} s(y)\right)}{c(\theta)}, \quad \forall y \in \mathcal{Y}
$$

![](ERGM%E7%BB%93%E6%9E%9C.png)



---

## 实证分析：模拟网络ERGM

- 表9中的估计结果表明，在5%的水平上，市值并不显著，这意味着机构的市值不会影响系统性风险网络的形成。商业银行的市值较高，但SI普遍较低。因此，我们应该更多地关注那些“相互联系太紧密而不能倒闭”的机构，而不是简单地“大而不倒”。


- 为了检验模型是否能很好地拟合系统性风险网络，我们使用ERGM对模拟网络和观测网络的特征差异进行了模拟和比较。从表中计算不同度数的平均p值，In度模拟网络与观测网络非常接近，这表明ERGM拟合良好。

![bg right:30% h:500](ERGM%E7%BB%93%E6%9E%9C2.png)

---

## 实证分析：风险排序

为了获得更具体的细节，我们进一步根据系统性风险贡献对单个机构进行量化和排名。根据股市的起伏分为四个时期：
1. 平静期，从2010年1月4日至2014年3月12日；
2. 牛市，2014年3月12日至2015年6月12日；
3. 股市崩盘，2015年6月12日至2016年1月27日；
4. 崩盘后时期，2016年1月27日至2017年12月31日。

在每个时期讨论单个机构的系统性风险贡献。仅在表11中列出了各时期系统性风险贡献最大的20家机构。此外，统计了四个时段前20家机构中每个部门的机构数量，结果如图5所示

---


## 实证分析：风险排序 cont.

我们注意到，商业银行在平静期和崩盘后时期的排名高于牛市和股市崩盘期间的排名。在第一阶段，排名前20位的商业银行数量为7家，而在第二和第三阶段，则下降到5家。商业银行为市场提供充足的流动性，市场价值较高。总的来说，中国的金融业是由商业银行主导的。这一现象可归因于当时政府领导的银行，即纾困减少了商业银行的系统性风险贡献。就券商而言，ES的系统性风险贡献最大，前20名券商的数量从第一阶段的4家增加到第二阶段的9家，表明牛市由券商主导。综合第5.2.2节的结果来看，券商不仅具有很强的尾部关联性，而且具有很高的系统风险贡献。他们的股价下跌将导致股市暴跌。此外，其他公司的系统性风险贡献也不容忽视。由于强尾部互联性，前20名中的其他公司数量保持在4或5家。就保险公司而言，前20名中四个子期的保险公司数量不超过4家，在第四期减少到0家。此外，我们注意到，系统性风险贡献率高的机构不一定是最大的。我们使用Kendall相关检验来检验金融机构的系统性风险贡献是否与其市值相关。从表12的测试结果中，我们发现第一期的p值小于0.1，这意味着金融机构的系统性风险贡献与其市值显著相关（在10%的水平上）。这可能是因为商业银行在第一阶段具有较高的市值和最大的系统性风险贡献。而在其他阶段，p值大于0.1。这一结果符合这样一个事实，即市值相对低于商业银行的券商在系统性风险贡献列表中排名第一。

---


## 结论