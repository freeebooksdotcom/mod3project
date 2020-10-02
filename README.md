# Match Me Matching You
by Anton Haugen

### Sources 
-Database <br>
http://www.stat.columbia.edu/~gelman/arm/examples/speed.dating/

# Introduction
Online dating is a $4 billion dollar industry. However many dating apps rely on photographs and shared interests. How accurately could a model predict successful dates, when both participants say yes to eachother, based on self-evaluation of personal attributes as well as predictions on what attributes the opposite gender would prefer.

# Data
Produced by the Columbia Business School from 2002-2004 for the study "Gender Differences in Mate Selection: Evidence From a Speed Dating Experiment," the data represents over four thousand unique four-minute dates that took place over twenty different speed dating events after which they would decide on whether they wanted to see the other person again. If both participants decided they wanted to see the other again, it would be a match. 

At the beginning of the event, they distributed 100 points across six attributes to describe their perfect mate. The six attributes were attractiveness, sincerity, intelligence, fun, ambition, and shared interests.

Though data was gathered at different points in the night and for three weeks after each event, the model just used data from the beginning of the night and the decision of both candidates as its target.

# EDA

Part of the EDA was seeing how participants, broken up by gender, evaluated themselves and each other and how this related to their match rate during the night.
![Image](images/intake_reason.png?raw=true)

# Modeling

What features the logistic regression and decision tree classifier decided were important was equally illuminating. 

As expected from the EDA, how 'fun' a man considered himself to be was the most important feature in the decision tree.

Surprisingly, in many of the logistic modelness how much a man judged attractiveness to be important to a woman (pattr2_1) had a much larger coefficient than how attractive the man considered himself to be or even how important a woman's attractiveness was to him in a potential match. In fact this latter category, 

# Conclusions
Part of the features engineered over the course of the modeling process aimed to capture how participants chose to distribute their points. The features 'female_balance'/'male_balance' returned true if all desired attributes had at least one point while the features 'male conformity'/'female conformity' gave a root mean square of how much a female's evaluations conformed to the male's predictions and vice versa. Interestingly, 'female conformity' had a much lower p-value than 'male conformity'. As each of these features improved the models' F1 score, in the future, I would like to explore how personality could be further gleaned from the attribute distributions.


