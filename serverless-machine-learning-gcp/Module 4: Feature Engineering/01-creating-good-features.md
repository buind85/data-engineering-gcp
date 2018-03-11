0:00
Previous lab was we took our Python code, we made it a module, we submit it to the cloud. It took longer, of course it takes longer because there's a whole bunch of infrastructure and everything to set up, so small problem, right? So, on small problems, the cloud run it and the cloud always takes longer. But that's okay, what we learned was how you could do it. And as you saw, it was primarily around packaging in Python and G-Cloud scripting.
0:26
Once you can write a tensor flow model, the rest of it is just a simple submission command. But we said that our goal is to basically get better then our heuristic role and we're not there yet, right. So that's the thing, at this point, what we still have is that original tensor flow model that we wrote. We've packaged it up, we've gussied it up, we've submitted it, great. But we still don't have anything that's better, so that's what we want to do now. So the last part that we want to look at is feature engineering, right. We'll look at feature engineering, which is basically how to basically get better features, so we get better models and better performance.
1:04
Now, what makes a good feature, right? You want to basically take your raw data, and you want to represent it in a form that's amenable to machine learning. So it has to be related to the objective, you don't want to just throw random data in there. That just makes the ML problem harder and the idea is to make the ML problem easier, right, make it easier for you to find the solution. So, if something is not related, throw it away. You have to make sure that it's known at production-time. This can be surprisingly tricky. We'll talk about some instances of this. It has to be numeric, it has to have enough examples, you need to have some human insights. So, let's talk about each of these things. So what makes a good feature? You want to basically take your raw data and you want to represent it in a form that's amenable to machine learning. So it has to be related to the objective, you don't want to just throw arbitrary data in there. Throwing arbitrary data just makes the machine learning problem harder, and the idea is to make the ML problem easier, make it easier for the ML model to converge towards a good solution. So if something isn't related, throw it away. You have to make sure that it's known at production time. This can be surprisingly tricky. We'll talk about some instances of how you might not know something at production time. It has to be numeric, and it has to have meaningful magnitude. You need to have enough examples. You need to have some human insights. So let's talk about each of these things. So first of all, a good feature needs to be related to what you're predicting. So you need to have some kind of a reasonable hypothesis of why a particular feature might matter for this particular problem. Don't just throw arbitrary data in there in the hope that there is some relationship somewhere. You don't want to do what's called data dredging. You don't want to dredge the large data set and find whatever spurious correlations exist. Because the larger the data set is, the more likely it is that there are lots of these spurious correlations. There is a famous study out there that found that the number of storks, this is a kind of bird, the number of storks is related to the number of babies that are born nine months later. So somebody went out counting the number of storks they saw in the trees, and then lo and behold, nine months later there were a lot more babies, if there are a lot of storks. I'm not joking. There's actually a Dutch study that found this correlation. Look it up. You don't want that to happen to your dataset though, because spurious correlations like these are not going to generalize. You should have some reasonable idea of why these things, the feature value and the outcome. You know the outcome, basically the thing that's represented by the label. You have to have some reasonable idea of why they could be related in some way. As a quick quiz, assume that you wanna predict the total number of customers who will use a discount coupon. Which of these are related. The font of the text in which the discount is advertised, yes or no? Yeah absolutely. The bigger the font the more likely it is to be seen, maybe. There is probably a difference between Comic Sans and Times New Roman. Some fonts are more trustworthy than others. So yeah, the font of the text in which the discount is advertised. Yes, it's probably a good feature. Price of the item the coupon applies to. Well, you can imagine that people use a coupon more if the item costs less. So yeah, could feature. But notice what I'm doing. I'm verbalizing my reason for using the feature. I'm not just saying yes or no for a particular feature. I'm saying "yes" because people may use a coupon more if the item is not highly priced. I'm saying "Yes" people might use a coupon more if they get to see it and you get to see it better if the font is bigger. You need to have a reasonable hypothesis for why a particular feature might be good. Number of items in stock. No, how would the user even know that. Sure, Out of stock versus in-stock. That could be a feature. But 800 items versus thousand items. No way. Let's take another example. Predict whether the credit card transaction is fraudulent or not. Whether the card holder has purchased these items at the store before, is that a good feature or is it not? Yes, it could be a feature. Is this a common purchase for this user or is it a completely unfamiliar unlikely thing? So yes, whether a card holder has purchased items at the store before that's probably a good feature. Credit card chip reader speed. What's the hypothetical relationship even? You don't want to use this as an input feature. Category of the item being purchased. Yes, there's probably some fraud committed- there's probably some fraud committed with things like television. Not as much fraud with things like shirts maybe. So you could imagine that there is a big different between different categories of items. So the category of the item could be a signal, a feature that you want to use in your model. Expiry date of the credit card. Probably not. Maybe the issue date because new credit cards experience more fraud but not the expiry date of the credit card. 