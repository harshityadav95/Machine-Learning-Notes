# Twitter Sentiment Classifier

### Supervised ML & Sentiment Analysis

In supervised machine learning, you usually have an input XX, which goes into your prediction function to get your \hat YY^. You can then compare your prediction with the true value YY. This gives you your cost which you use to update the parameters \thetaθ. The following image, summarizes the process.![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/3vVQr0zhTlW1UK9M4V5Vww_e5b656e0d36041e1be5edd54bd3562a5_Screen-Shot-2020-09-01-at-7.35.25-AM.png?expiry=1602288000000&hmac=1172k2xB1szrzkR1FuVVnATQwvCMR3AHZff_kK4DqME)

To perform sentiment analysis on a tweet, you first have to represent the text \(i.e. "I am happy because I am learning NLP "\) as features, you then train your logistic regression classifier, and then you can use it to classify the text.![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/z84yBRbCS0qOMgUWwktKdA_927d67ce246c4212ad9d389a0243ed0e_Screen-Shot-2020-09-01-at-7.41.26-AM.png?expiry=1602288000000&hmac=p5PZPQjCPnWbWV5KuHqfNx1NoYlHA52qFSGqZDm3Q3g)

Note that in this case, you either classify 1, for a positive sentiment, or 0, for a negative sentiment.

### Vocabulary & Feature Extraction

Given a tweet, or some text, you can represent it as a vector of dimension VV, where VV corresponds to your vocabulary size. If you had the tweet "I am happy because I am learning NLP", then you would put a 1 in the corresponding index for any word in the tweet, and a 0 otherwise.![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/vpVZPKHCS6uVWTyhwmurrQ_d2e2fd874a354ab38047ef531021b681_Screen-Shot-2020-09-01-at-7.48.25-AM.png?expiry=1602288000000&hmac=laLcVMl_BybS16GTgneDU8UW9QMeTQ3dYrfiUJxXLrw)

As you can see, as VV gets larger, the vector becomes more sparse. Furthermore, we end up having many more features and end up training \thetaθ VV parameters. This could result in larger training time, and large prediction time.

### Feature Extraction with Frequencies

Given a corpus with positive and negative tweets as follows:![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/zhNAjggWTbWTQI4IFu21ZA_32f86a38bc224959be21ede407128c82_Screen-Shot-2020-09-01-at-7.55.08-AM.png?expiry=1602288000000&hmac=KmFWBwdcFaufPclox8ObuXx-beO08cFYuFmCk98ZKmY)

You have to encode each tweet as a vector. Previously, this vector was of dimension VV. Now, as you will see in the upcoming videos, you will represent it with a vector of dimension 33. To do so, you have to create a dictionary to map the word, and the class it appeared in \(positive or negative\) to the number of times that word appeared in its corresponding class.![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/vhHO7A7dTvuRzuwO3U779Q_5364f83a7bd54782a09279efe06e96f2_Screen-Shot-2020-09-01-at-7.57.30-AM.png?expiry=1602288000000&hmac=SquhxWd2Xc707q8ZSobPzbIg9-WLPwEUyDSBmNdZrkI)

In the past two videos, we call this dictionary \`freqs\`. In the table above, you can see how words like happy and sad tend to take clear sides, while other words like "I, am" tend to be more neutral. Given this dictionary and the tweet, "I am sad, I am not learning NLP", you can create a vector corresponding to the feature as follows:![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/N_PzQkNvSNqz80JDb-ja5A_a44a87942c5e476593cd8e1582cf5b06_Screen-Shot-2020-09-01-at-8.04.10-AM.png?expiry=1602288000000&hmac=uXBO3IuwS13f-5CVYNDuI3XgWPkww_sn2g27P_Ur_Q4)

To encode the negative feature, you can do the same thing.![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/dQU0vX1NT3yFNL19TS98gQ_b885bb87a6d644389726ddc740869153_Screen-Shot-2020-09-01-at-8.04.21-AM.png?expiry=1602288000000&hmac=A2wcwnbkl1LOgGltuzc4ZQS-oHO1HBsVDNTtQcsHFQY)

Hence you end up getting the following feature vector \[1,8,11\]\[1,8,11\]. 11 corresponds to the bias, 88 the positive feature, and 1111 the negative feature.

### Preprocessing

When preprocessing, you have to perform the following:

1. Eliminate handles and URLs
2. Tokenize the string into words.
3. Remove stop words like "and, is, a, on, etc."
4. Stemming- or convert every word to its stem. Like dancer, dancing, danced, becomes 'danc'. You can use porter stemmer to take care of this.
5. Convert all your words to lower case.

For example the following tweet "@YMourri and @AndrewYNg are tuning a GREAT AI model at https://deeplearning.ai!!!" after preprocessing becomes![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/dKnqOOtTQP6p6jjrU2D-LQ_3e6a23c4313b481f9301bbba086b6f66_Screen-Shot-2020-09-01-at-8.14.55-AM.png?expiry=1602288000000&hmac=ZtNPGtYvc48y10KNY1PlPADoj0CW8eOl-xd0IOxga30)

\[tun, great, ai, model\]\[tun,great,ai,model\]. Hence you can see how we eliminated handles, tokenized it into words, removed stop words, performed stemming, and converted everything to lower case.

### Putting it all together

Over all , you start with a given text, you perform preprocessing, then you do feature extraction to convert text into numerical representation as follows:![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/_OTVrbipS9ek1a24qXvXFw_641fc5c72d974a4582c229f6ebf073f5_Screen-Shot-2020-09-01-at-8.20.08-AM.png?expiry=1602288000000&hmac=Zx3uOWFDZMx-ssp8cRm7ajRG2Hhw3wYxFSDeVQy5HPs)

Your XX becomes of dimension \(m,3\)\(m,3\) as follows.![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/C3BC-AlDRj-wQvgJQyY_8w_6b189b0ef72e456b9cce8c264796f567_Screen-Shot-2020-09-01-at-8.24.17-AM.png?expiry=1602288000000&hmac=-nOINqDPRZdylhBu0cpMbTvFzb8XjShcUxtwb3ev8VQ)

When implementing it with code, it becomes as follows:![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/NwmjyOjKQTaJo8joyqE2Ow_330a68fd246c44c3a5409216b096559c_Screen-Shot-2020-09-01-at-8.20.48-AM.png?expiry=1602288000000&hmac=nIhysw08frGE5yQNlrDowavo6BREJm8cYwj1L1Orqh4)

You can see in the last step you are storing the extracted features as rows in your XX matrix and you have mm of these examples.

### Logistic Regression Overview

Logistic regression makes use of the sigmoid function which outputs a probability between 0 and 1. The sigmoid function with some weight parameter \thetaθ and some input x^{\(i\)}x\(i\) is defined as follows.![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/oL4Ox_JxTBi-DsfycUwYvw_d0582a0dddf7470486f0955c8b025dd6_Screen-Shot-2020-09-01-at-8.30.00-AM.png?expiry=1602288000000&hmac=3Ff2led-r04hc7da1J8EvO_Wh870RrBNaj3NPSFmto4)

Note that as \theta^Tx^{\(i\)}θTx\(i\) gets closer and closer to -\infty−∞ the denominator of the sigmoid function gets larger and larger and as a result, the sigmoid gets closer to 00. On the other hand, as \theta^Tx^{\(i\)}θTx\(i\) gets closer and closer to \infty∞ the denominator of the sigmoid function gets closer to 1 and as a result the sigmoid also gets closer to 11.

Now given a tweet, you can transform it into a vector and run it through your sigmoid function to get a prediction as follows:![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/THV0BbogT2i1dAW6IA9oMg_67bcc86617b54ac4b5750d51d032cd8f_Screen-Shot-2020-09-01-at-8.37.07-AM.png?expiry=1602288000000&hmac=YpOSqb9BUb7_DK5v1Z_OLy2htRyuvtqA2BIxCe1_B1Y)

### Logistic Regression: Testing

To test your model, you would run a subset of your data, known as the validation set, on your model to get predictions. The predictions are the outputs of the sigmoid function. If the output is \geq =0.5≥=0.5, you would assign it to a positive class. Otherwise, you would assign it to a negative class.![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/xq8RYoHvROKvEWKB73TiUg_ac2e78d0c6654f58ab40822d08b68465_Screen-Shot-2020-09-02-at-10.47.33-AM.png?expiry=1602288000000&hmac=t_jz4172iRsVQDMM6eRpuZGuv_b3aahL3pO6hVUeOuY)

In the video, I briefly mentioned XX validation. In reality, given your XX data you would usually split it into three components. X\_{train}, X\_{val}, X\_{test}Xtrain​,Xval​,Xtest​. The distribution usually varies depending on the size of your data set. However, an 80,10,1080,10,10 split usually works fine.

To compute accuracy, you solve the following equation:![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/1NW_9EVkS6yVv_RFZGusFA_90304c432911444eb5f981a4aaa97c47_Screen-Shot-2020-09-02-at-10.53.31-AM.png?expiry=1602288000000&hmac=boGhdC5RLoeqiPfjHM8FQapFrFmRjEkXSNIsEh_yEXg)

In other words, you go over all your training examples, mm of them, and then for every prediction, if it was wright you add a one. You then divide by mm.  


