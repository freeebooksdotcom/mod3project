# Match Me Matching You
by Anton Haugen

### Sources 
-Database <br>
http://www.stat.columbia.edu/~gelman/arm/examples/speed.dating/

## Introduction
Online dating is a $4 billion dollar industry. However many dating apps rely on photographs and shared interests. How accurately could a model predict successful dates, when both participants say yes to eachother, based on self-evaluation of personal attributes as well as predictions on what attributes the opposite gender would prefer.

## Data
Produced by the Columbia Business School from 2002-2004 for the study "Gender Differences in Mate Selection: Evidence From a Speed Dating Experiment," the data represents over four thousand unique four-minute dates that took place over twenty different speed dating events after which they would decide on whether they wanted to see the other person again. If both participants decided they wanted to see the other again, it would be a match. 

At the beginning of the event, they distributed 100 points across six attributes to describe their perfect mate. The six attributes were attractiveness, sincerity, intelligence, fun, ambition, and shared interests.

Though data was gathered at different points in the night and for three weeks after each event, the model just used data from the beginning of the night and the decision of both candidates as its target.

## EDA

Part of the EDA was seeing how participants, broken up by gender, evaluated themselves and each other and how this related to their match rate during the night.
![Image](images/attractionscores.png?raw=true)
Attractiveness was one of the most important attributes.
Two hypothesis tests were carried on both gender's predictions of how important attractiveness was to the opposite gender. In both cases the null hypothesis was rejected. However, it should be considered that the importance of attraction was made as what was important to each individual while the predictions pertained to group trends.

A two proportion t-test also showed that men who rated themselves 10 on attractiveness matched in a greater proportion than women who rated themselves 10.

![Image](images/funscores.png?raw=true)
In constrast, the predictions on the importance of fun was to the opposite sex was a closer match to score distributions when compared to attractiveness. In addition, how fun a man thought he was a better predictor for likelihood of a match than how attractive he thought he was.

![Image](images/sincerity.png?raw=true)
In analyzing the average score for matches and non-matches, men who placed more value in fun matched more than those who valued sincerity and shared interests. Surprisingly, women underestimated the value of sincerity to men. 

## Modeling

What features the logistic regression and decision tree classifier decided to emphasize was equally illuminating. 

![Image](images/model_coefficients.png?raw=true)

As expected from the EDA, how 'fun' a man considered himself to be was the most important feature in the decision tree.

Surprisingly, in many of the logistic modelness how much a man judged attractiveness to be important to a woman (pattr2_1) had a much larger coefficient than how attractive the man considered himself to be or even how important a woman's attractiveness was to him in a potential match. In fact this latter category would move the model to predict the non-match class (pf_o_att)

Of further interest, most of the coefficients pertained to what the female partner wanted and what the male partner thought the female wanted. For example, how important the male thought ambition was to the female (pamb2_1) had a much larger coefficient than how the male evaluated his ambition (pamb3_1), which was the same case for intelligence (pintel2_1) and sincerity (psinc2_1).

## Features and Future Modeling
Part of the features engineered over the course of the modeling process aimed to capture how participants chose to distribute their points. The features 'female_balance'/'male_balance' returned true if all desired attributes had at least one point while the features 'male conformity'/'female conformity' gave a root mean square of how much a female's evaluations conformed to the male's predictions and vice versa. Interestingly, 'female conformity' had a much lower p-value than 'male conformity'. As each of these features improved the models' F1 score, in the future, I would like to explore how personality could be further gleaned from the attribute distributions.

## Conclusions
The final predictive model, a random forest classifier with 900 estimators and a max depth of 7, had shown great improvement as more 'personality' features were engineered though it had a final f1 score of roughly 0.4. In the future, I would like to improve normalization of each attribute score centering it on the average for each gender and use a less rigorous metric to evaluate models since a false positive only means a bad recommended match. The researched placed a lot of emphasis on race in their experiment's evaluation criteria even though their dataset was overwhelmingly white. I would like to explore the implications of race on matching in a future model. Hopefully, I will also build a recommendation engine around attribute scoring.

