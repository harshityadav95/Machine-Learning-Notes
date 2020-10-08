# Twitter Sentiment Classifier

### Supervised ML & Sentiment Analysis

In supervised machine learning, you usually have an input XX, which goes into your prediction function to get your \hat YY^. You can then compare your prediction with the true value YY. This gives you your cost which you use to update the parameters \thetaθ. The following image, summarizes the process.![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/3vVQr0zhTlW1UK9M4V5Vww_e5b656e0d36041e1be5edd54bd3562a5_Screen-Shot-2020-09-01-at-7.35.25-AM.png?expiry=1602288000000&hmac=1172k2xB1szrzkR1FuVVnATQwvCMR3AHZff_kK4DqME)

To perform sentiment analysis on a tweet, you first have to represent the text \(i.e. "I am happy because I am learning NLP "\) as features, you then train your logistic regression classifier, and then you can use it to classify the text.![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/z84yBRbCS0qOMgUWwktKdA_927d67ce246c4212ad9d389a0243ed0e_Screen-Shot-2020-09-01-at-7.41.26-AM.png?expiry=1602288000000&hmac=p5PZPQjCPnWbWV5KuHqfNx1NoYlHA52qFSGqZDm3Q3g)

Note that in this case, you either classify 1, for a positive sentiment, or 0, for a negative sentiment.

