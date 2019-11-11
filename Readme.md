# MGT 432 COURSE PROJECT 
---

## Background

__Initial Public Offering:__  An _Initial Public Offering_ (IPO) is a process by which a _private_ company becomes a _public_ company. The private company issues new equity ownership shares and then sells them to an initial set of investors. Those investors can then trade the shares on a public stock exchange (the "open market"), and anyone can continue to buy or sell shares of the company on the exchange. 

__IPO Proceeds:__ To place the offering, the company going public typically hires an investment bank (also know as the "underwriter") to sell the initial shares to early investors, who then can either hold onto the shares or go to the open market and sell them. In return for the shares, the company receives back cash -- known as the total "IPO Proceeds."  

__Setting an Initial Price for Shares:__ There is a great deal of uncertainty as to what the price should be for new shares. If the the investment bank sets an initial price that is too high, then the share-price will fall on the first day of trading and the investors who bought the initial shares will lose money. If the investment bank sets an initial price that is too low, then the share-price will begin to rise on the first day of trading, the initial investors can immediately make considerable profits, but the issuing will lose out on funds (IPO Proceeds) that it otherwise could have collected if the initial price had been set higher. The investment bank for the IPO, therefore, faces a difficult problem with respect to predicting an appropriate price to sell initial shares to initial investors. 

__Investment Bank Reputaion:__  Failure to predict the price correctly can lead to a loss of reputation for the bank by either the investors buying shares, and/or the companies hiring the bank to go public. Both the buy-side and sell-side of the transaction therefore consider the reputation of the investment bank when entering into the transaction; if the bank gets the price too far wrong (either too high, or too low), then that will hurt the reputation and future prospects of the bank. To help you potentially model this factor, we provide you with some proxy measures of investment reputation.

__Under-Pricing:__ Although ideally investment banks might want to hit the exact right price, typically it is observed that banks will offer shares to the initial buyers at a somewhat lower price than they actually predict the stock to trade at on the first day. The first-day appreciation in the stock price is typically viewed as a "risk premium" that is required to compensate the first investors for taking on the risk of buying shares when they do not truly know the public value of those shares on an open market. This tendency to underprice the initial offer price is referred to as "under-pricing." It is believed that issuing companies accept a certain amount of under-pricing as just a necessary cost of going public. Nevertheless, the issuing company also clearly wants to minimize that cost and raise the most proceeds possible, and so the issuing company also has an interest in making their own prediction of what they think the stock will trade at once it goes public and using that in negotiaions with their Investment Bank.

__First-Day IPO Stock Price Appreciaition or Loss:__ Based on all of the above, one can conclude that a prediction of what will happen to the stock price on the first day of trading is a very important and valuable prediction for all involved. The issuing company wants an accurate predicition because that helps them to maximize the amount of capital that they can raise from the IPO; the investment bank wants an accurate predicition in order to better server their clients; and the initial institutional investors want an accurate predicition so that they can predict their arbitrage opportunity and the money they think that can make for assuming the risk of buying into the initial offering when there is no market price yet). The point of this project, therefore, is to make predicitions about the first-day IPO stock price appreciaition or loss. The type of predicition, and the weighting of the outcome, however, can be done numerous different ways - so you will explore that in the sections that follow.

__More Information:__ For more information on the IPO process, we have provided you with a copy of ___The Initial Public Offering Handbook: A Guide for Entrepreneurs, Executives, Directors and Private Investors___ by Sonny Allison Chris Hall David McShea and with Special Contributing Author Katherine VanYe and Contributing Authors from Perkins Coie LLP in the project resources directory. For students interested in the theoretical aspects of "IPO Underpricing" and why it happens, we have provided you with a copy of the article __Why Has IPO Underpricing Changed Over Time?__ by Tim Loughran and Jay Ritter (Financial Management, Autumn 2004, pages 5 - 37).

## The Prediction Problem  

You will need to predict whether the price of each IPO stock will go up (or down) on the first day of trading.  The first-day movement in the IPO stock price can be quantified in many different ways:  

  * as a dummy variable (i.e., 1 or 0) based on whether the price of the stock goes up on the first day of trading; 
  
  * as the actual amount that the IPO stock price changes on the first day of trading;  
  
  * as the percent change in the IPO stock price on the first day of trading (i.e., the first-day stock "return"); 
  
  * as the probability that the IPO stock price will change in a given direction on the first day of trading;
  
You will need to define, calculate, and use the appropriate measure based on the nature of the question(s) being addressed in the sections below. Predictions should be evaluated by the standard metrics covered in class, and in some cases you may be asked to evaluate the prediction with some other, custom scoring method.

## Data

Managers of a company going public work with their accountants, lawyers, and investment bank to prepare a disclosure document called the "IPO Prospectus" (specifically, SEC Form 424b). The prospectus includes all of the information about their business, management, financial performance, etc., up to the point of the IPO. The company must file the prospectus with the government and provide it to every investor that considers investing into the IPO.  Although companies might not want to fully disclosure all aspects of their business, or risk factors related to their business, in the Prospectus -- they nevertheless need to do so (at least to some degree) to avoid lawsuits from investors that are harmed by witholding material information. 

Much of the data that you will use was extracted from the IPO Prospectus. We also merge in data from other investment research companies such as SDC (these companies research and track startup ventures and companies going to IPO in order to sell that information to potential investors for analysis). We have compiled that data together into two Excel spreadsheet files. We also provide a document that defines each variable. This is real, raw, and messy data - so you need to inspect the data, run descriptive statistics for all of variables, and then clean, transform, recalculate, interpolate, and do whatever else you think need to do to the data in order to improve your predictions.  

__Can we look for new data and "supplement" the Data that you provided?__ 

__No.__ The problem is that you may find supplemental data that picks up information from the future (i.e., from _after_ the IPO), and then be using the future to predict the past. To prevent that, all teams must use only data/information provided to you in the Excel spreadsheet.

The data is provided in two files. 

  1. `IPO_data_to_learn.xlsx`  

  You will use `IPO_data_to_learn.xlsx` for all of your predictive modeling (data exploration, variable transformation, model cross-validation, and model testing). 
    
  2. `IPO_data_to_predict.xlsx`  

  You will use `IPO_data_to_predict.xlsx` to record your predictions for a hold-out set of data where you do not know the outcome. Put your predicted values in the columns for `P1`, `P2`, `P3`, `P4`, `P5`, `P6`, `P7`, `P8`, `P9` - which are currently empty. We will evaluate your models based on their preformance in predicting these cases. The file is identical to `IPO_data_to_learn.xlsx`, except that it is missing data for the closing price at the end of day one. 


#### Key Variables

We provide a definition of all variables in the file `Variables.pdf`. It might be beneficial, however, to do some additional reading about the purpose of each variable. Particularly important variables are:

  * __rf__: Companies are required to disclose all of the known and material, internal or external risk factors that could affect the future performance of the company. This information is contained in a “Risk Factors” section of the IPO prospectus. We have parsed out that section for you and provide you the raw text to model with text analysis, as you see best. 

  * __offerPrice__: The price at which a company offered shares to the initial investors of the IPO.  

  * __closeDay1__: The price at which shares eventually trade, measured at the end of the first day of trading.  


## Grading

We will create an individual git repo for you and your team to use for this project. Start a Jupyter notebook for your project and divide it into logical sections. Document all of your logic, processing, methods, models, and results in your notebook. We expect that you will include many (or even all) of the different methods and models that you have learned in the class, as appropriate. 

For example, you will want to show:

  * data cleaning and preprocessing 
  * feature extraction 
  * feature reduction
  * training, tuning, and testing of each model (as appropriate)
  * pipelining and hyper-parameter tunining (as appropriate)
  * baseline model comparisons
  * advanced model comparisons between different model typre
  * ensembles
  * descriptions and explanations of which model is best for each predicition problem 
  * discussion of additional tasks or improvements that might boost performance

Your grade for the project will be based on the entire process of getting to your predictions, as well as the quality, thoroughness, organization, logical progression, attempted modeling variations, and persuasiveness of your Jupyter notebook. The evaluation is NOT based on just the raw prediction performance on the holdout data. So be sure to develop a rich and insightful Jupyter notebook. 

Also use your Jupyter notebook to generate the tables, charts and graphs that you will use in your classroom presentation, so we can corss-reference and see exactly what you have done. Try to communicate your results in a clear and concise manner with appropriate illustrations.  


### Tips

* Take some time to educate yourself about the IPO process. Understanding how the data and variables relate to real-world outcomes will help you, givern that this is real-world data.  

* We make no guarantees about the quality, completeness, or appropriateness of any of the data. Again, this is real-world data! So work with it as you see best.   
  
* Document your assumptions (e.g., the evaluation metric you are using, any hyper-parameters that you are tuning, etc.).

* Document your code. Document steps that are not obvious by looking at just the code. If in doubt, document more (not less).

* Give variables meaningful names. 

* To speed up experimentation as you start to code long-running models, you might want to extract a small, random sample from the original dataset - until you get your code working. 

* To speed up runtime on long-running models, try to use all of your CPU cores by setting the option of n_jobs = -1 (when that option is available). 

* To make sure all results are reproducible, set a random seed whenever possible.  

* Be creative -- but don't forget that you need to explain your reasoning.

* Present your results as a story. Develop a storyline, using sections of markdown text to explain what you are doing and why.  

* Your final grade is based on the entire process of completing the project -- not just based on your prediction results on the unseen data. 

* __Your code must be able to be run, with everything it needs in just one directory.__ 

### Should you cheat? No.

Everything you do on this project must be your own work. __You may not collaborate with any other individual or team on this project.__

Note that a similar version of this problem was used last year. You should not refer to any previous work - doing so will be considered cheating with respect to your own project. Moreover, important aspects of both the data and the prediction problem have changed since last year, and so doing so will likely hurt your progress within the project, but even more importantly likely reveal that you have cheated by attempting something that only made sense in previous years. 



## Prediction Problems

For each of the problems listed below, make a prediction and place it in the appropriate column (named as `P1`, `P2`, `P3`, `P4`, `P5`, `P6`, `P7`, `P8`, `P9`) in the `IPO_data_to_predict.xlsx` file. We have intentionally provided you with data in an Excel format - so please submit your predictions in Excel Format. As a nice flourish, try to place your predictions back into the same file that you received (i.e., in to the same file with the same formatting) - that is something that you might have to do in the workplace (this step, however, is not required - if you find this difficult, just you can also dump your results into a new Excel spreadsheet with appropriately named columns). 

For each prediction, be sure to also show appropriate evaluation metrics in your Jupyter notebook. Show the standard metrics presented in class, but also the custom metrics given to you for problems 7, 8, and 9. 

Commit and push your predictions (along with your final jupyter notebook file) as part of your project repository. 

### Prediction P1  

  * Predict whether the closing price at the end of the first day of trading will go up (the "positive" case, coded as 1) or down (the "negative" case, coded as 0) from the offer price. You may use all data from the dataset __except for__ the `rf` variable (i.e., risk factors). 

### Prediction P2

  * Predict whether the closing price at the end of the first day of trading will go up (the "positive" case, coded as 1) or down (the "negative" case, coded as 0) from the offer price. You may use __only__ the `rf` (i.e., risk factors), `year`, and `industryFF12` variables for this prediction task. You may, however, perform additional text analysis of the `rf` variable. 

### For all remaining problems, you may use any or all of the features.

### Prediction P3

  * Predict whether the closing price at the end of the first day of trading will go up (the "positive" case, coded as 1) or down (the "negative" case, coded as 0) from the offer price. 

### Prediction P4

  * Predict whether the closing price at the end of the first day of trading will go __up__ by more than 20% from the original offer price (the "positive" case, coded as 1) or not (the "negative" case, coded as 0).  

### Prediction P5

  * Predict whether the closing price at the end of the first day of trading will go __down__ by more than 20% from the original offer price (the "positive" case, coded as 1) or not (the "negative" case, coded as 0).    

### Prediction P6
  
  * Predict the share price at the end of the first day. 

### For the remaining problems, provide a ___predicted probability___ (expressed as a number from 0 to 100) that the stated event will happen. 

### Prediction P7

  * Predict the probability that the closing price at the end of the first day of trading will go __up__ by more than 5% from the original offer price.  

  __Scoring Metric for P7:__ Your predictions will be evaluated in the following manner (where scored points are bad). For every observation, make a predicted probability, p, ranging from 0 to 100. For predictions where the event turns out to be FALSE, a score of p * p (i.e., the square of your predicted probability for that event) will be assessed. For predictions where the event turns out to be TRUE, a score of (100 - p) * (100 - p) will be assessed (i.e., the square of 100 minus your predicted probability for that event). Attempt to tune you prediction model(s) accordingly.
  
  For example: If you predict 70 for an observation that ends up being FALSE, then the score for that observation would equal 4,900 (70 * 70 = 4,900); but if you predict 70 for an observation that ends up being TRUE, then the score for that observation would equal 900 (100 - 70 = 30, and 30 * 30 = 900).

### Prediction P8

  * Predict the probability that the closing price at the end of the first day of trading will go __up__ by more than 50% from the original offer price.  

  __Scoring Metric for P8:__ Same scoring metric as __P7__ above. Attempt to tune you prediction model(s) accordingly.

### Prediction P9

  * Predict the probability that the closing price at the end of the first day of trading will go __down__  (the "positive" case, coded as 1) or not (coded as 0) by more than 10% from the original offer price.  

  __Scoring Metric for P9:__ Your predictions will be evaluated in the following manner (where scored points are bad). For every observation, make a predicted probability, p, ranging from 0 to 100. For predictions where the event turns out to be FALSE, a score equal to p will be assessed. For predictions where the event turns out to be TRUE, a score of 2 * (100 - p) will be assessed. Attempt to tune you prediction model(s) accordingly.
  
  For example: If you predict 70 for an observation that ends up being FALSE, the score for that observation would equal 70; but if you predict 70 for an observation that ends up being TRUE, then the score for that observation would equal 2 * (100 - 70) = 60. 
