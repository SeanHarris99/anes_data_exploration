<div class="container-fluid main-container">

<div class="fluid-row" id="header">

# How do economic factors shape voting patterns?

### An exploration of ANES cumulative time series data.

#### Sean Harris

</div>

<font size="4">0\. Introduction</font>  
The ANES dataset contains survey responses about the topic we are interested in. These range back to 1948, and not every question was asked every year, so the data we use are compilations of many different questions from different years. With that in mind, some simple and interesting relationships can be found between economic status and voting behavior.

<font size="3">0.1 Loading Libraries and Data</font>  
First the necessary packages are installed and loaded with the pacman package. Then the ANES data is loaded from a .sav file with the haven package.

<font size="3">0.2 Preparing Variables</font>  
A new data variable, anes_use, is created to hold results of the survey questions we are interested in.

<font size="4">1\. How does income affect voting behavior?</font>

<font size="3">1.1 Income over time</font>  
First we will look at how different income brackets vote. The ANES data-set contains questions which surveyed respondee's self-reported income as being either: 1\. 0-16 percentile, 17-23 percentile, 34-67 percentile, 68-95 percentile, and 96-100 percentile.

 ![Alt text](figs/income.PNG?raw=true "Title2")
  
At a glance, some patterns are clear: less wealthy people vote far less than the wealthy, and tend to vote less Republican. Other interesting artifacts can be observed, like 1992's third party vote being concentrated in the middle to upper-middle class bracket.

<font size="3">1.2 Aggregated income</font>  
These patterns become more obvious when all years are aggregated together, and we look at total votes for a given party per income group.

 ![Alt text](figs/income_net.PNG?raw=true "Title2")


We see three patterns: 1\. Democratic vote is roughly constant across income groups, 2\. Republican vote grows with income, 3\. Nonvoting grows with poverty.

<font size="3">1.3 Regression Analysis</font>  
We can see if these three patterns can be made more concrete with a linear regression analysis.

 ![Alt text](figs/wealth_regression.PNG?raw=true "Title2")

The three patterns appear to hold. There is no clear linear relationship between income and democratic vote. And there is a strong linear positive correlation between income and Republican vote, and a strong linear negative correlation for nonvoters.  
The regression suggests a 1-percentile increase in wealth correlates with a .36% increase of Republican vote and a .33% decrease in abstaining from voting. While this relationship is strong, it is not necessarily causal, and it is important to keep in mind confounding variables like race or geography that are not the focus of this analysis.

Since the wealthy appear to vote strongly Republican, we can look at how the rich vote changes over time.

 ![Alt text](figs/rich_vote.PNG?raw=true "Title2")


It appears that the proportion of the wealthy (96+ percentile) voting Republican has consistently decreased since 2000\. Infact, 2016 saw the lowest proportion of wealthy voting Republican in the entire dataset: 34% in 2016, where the dataset mean is 59%.

<font size="4">2\. How does occupation affect voting behavior?</font>  
If the wealthy are growing less Republican, a look at the relationship between one's profession and voting behavior could give deeper insight.


 ![Alt text](figs/occupations.PNG?raw=true "Title2")


At a glance, we can see how higher-salary Professional and Managerial occupations have much higher voter turnout, while lower-salary Laborers have very low turnout.  
We can do a linear regression analysis to see if higher-salary occupations are becoming less Republican, as the data so far has suggested.

 ![Alt text](figs/pmc.PNG?raw=true "Title2")



The regression suggests Professional and Managerial voters have grown increasingly Democratic since the 70s. As expected, this wealthier cohort has trended liberal over time. This is just one group, and further analysis into the connection with education and urbanism could be interesting.

</div>

<script>// add bootstrap table styles to pandoc tables function bootstrapStylePandocTables() { $('tr.odd').parent('tbody').parent('table').addClass('table table-condensed'); } $(document).ready(function () { bootstrapStylePandocTables(); });</script> <script>$(document).ready(function () { window.buildTabsets("TOC"); }); $(document).ready(function () { $('.tabset-dropdown > .nav-tabs > li').click(function () { $(this).parent().toggleClass('nav-tabs-open') }); });</script> <script>(function () { var script = document.createElement("script"); script.type = "text/javascript"; script.src = "https://mathjax.rstudio.com/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML"; document.getElementsByTagName("head")[0].appendChild(script); })();</script>