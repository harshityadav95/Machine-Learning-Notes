# Bayes’ Rule

### Bayes' Rule

Conditional probabilities help us reduce the sample search space. For example given a specific event already happened, i.e. we know the word is happy:![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/xoYzIfcHT0uGMyH3B69LQw_3b10c11c4a504416b8ea133f0c974995_Screen-Shot-2020-09-08-at-1.23.56-PM.png?expiry=1602460800000&hmac=3EhEL1eIleJR6gVvDAvhMPtkkA4gte__2TJjEldYYFE)

Then you would only search in the blue circle above. The numerator will be the red part and the denominator will be the blue part. This leads us to conclude the following:![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/gXRnWNLHSOy0Z1jSx3jscg_b2c28038bf054638a38ef02a1ac7705f_Screen-Shot-2020-09-08-at-1.28.57-PM.png?expiry=1602460800000&hmac=_jOx3UGPVamaU0dmMRy8oEmGZeC-catHP3zmXRsnXFw)

Substituting the numerator in the right hand side of the first equation, you get the following:![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/0Jl5aETpQImZeWhE6bCJrg_5d5d25924694451fa3eae308da6440c2_Screen-Shot-2020-09-08-at-1.32.01-PM.png?expiry=1602460800000&hmac=SRLXOhUNjsTq5P6PgVGxZXXsQGTGK4MYXSSEROwUUgs)

Note that we multiplied by P\(positive\) to make sure we don't change anything. That concludes Bayes Rule which is defined as

P\(X\|Y\) = \frac{P\(Y\|X\) P\(X\)}{P\(Y\)}P\(X∣Y\)=P\(Y\)P\(Y∣X\)P\(X\)​.

### Naive Bayes Introduction

To build a classifier, we will first start by creating conditional probabilities given the following table:![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/fwihrJk_RSGIoayZPxUhTQ_3cd35492d526492dbcae2e4baa02bdf4_Screen-Shot-2020-09-08-at-3.38.05-PM.png?expiry=1602547200000&hmac=RpfKzCtoz4xR_9gOKWOOCgCbAkENz7tIqi5eFnPWNPk)

This allows us compute the following table of probabilities:![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/Iiek1X0pSX6npNV9KXl-NQ_2945fa3844184948b0a2590d0683b4f8_Screen-Shot-2020-09-08-at-3.41.46-PM.png?expiry=1602547200000&hmac=v4ejhzDFRebtcXrTsVitp73BFQnkSfKSZXarVGL-pIM)

Once you have the probabilities, you can compute the likelihood score as follows![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/nc3XUyPHSgyN11Mjx7oMNQ_d2a00c93d29b497bba81a3944072feb9_Screen-Shot-2020-09-08-at-3.43.07-PM.png?expiry=1602547200000&hmac=Hn9N5_uJh2UGfypgNgXePRAd4J3L4x_3DW-ausYeEfg)

A score greater than 1 indicates that the class is positive, otherwise it is negative.

###  Log Likelihood, Part 1 <a id="log-likelihood-part-1"></a>

‌

To compute the log likelihood, we need to get the ratios and use them to compute a score that will allow us to decide whether a tweet is positive or negative. The higher the ratio, the more positive the word is:​![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/jRdwvis8SNCXcL4rPMjQlg_d8b30951c82b4b9f8f20b8f0e56d0a83_Screen-Shot-2020-09-08-at-4.01.25-PM.png?expiry=1602547200000&hmac=E02nZ-tlIh4eN9vI98nZ-jA9gICUQYH_q15qVzIkWJg)​​![](https://gblobscdn.gitbook.com/assets%2F-MJ0Zq3ebnnCuonyonEY%2F-MJLhFTkKdTT-jdZG-aA%2F-MJLnNKoJ9L3U4Eb_U7H%2Fimage.png?alt=media&token=60110250-d9e7-4d08-a9a4-ec91509392eb)​![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/I1jOUPkpSRmYzlD5KSkZUg_8d00fbc64ac94b9a9d9c41d367288447_Screen-Shot-2020-09-08-at-4.10.13-PM.png?expiry=1602547200000&hmac=qIUvVakg2SjnGDIU__zNIclelY8W8B6R9V1fP0Hzg6w)‌

Having the \lambdaλ dictionary will help a lot when doing inference.‌

### Log Likelihood Part 2 <a id="log-likelihood-part-2"></a>

‌

Once you computed the \lambdaλ dictionary, it becomes straightforward to do inference:​![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/lqWbkNaCS5alm5DWgvuWoQ_2d4cdfc82bf142f08b89cb49f2908ef8_Screen-Shot-2020-09-08-at-4.17.43-PM.png?expiry=1602547200000&hmac=64kQox2rzZ13upN-wHXyyLD6jDokrCUbYQj2i3G6cXg)​‌

As you can see above, since 3.3 &gt; 03.3&gt;0 , we will classify the document to be positive. If we got a negative number we would have classified it to the negative class.​![](https://gblobscdn.gitbook.com/assets%2F-MJ0Zq3ebnnCuonyonEY%2F-MJLhFTkKdTT-jdZG-aA%2F-MJMAt08jrLOF3iP91_0%2Fimage.png?alt=media&token=f8065c4a-13a9-4a28-afca-8bf3f36c66de)‌

### Testing naïve Bayes <a id="testing-naive-bayes"></a>

​![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/DBzYqctbQdSc2KnLW5HURA_3de7717134ec4f3ea36f9318083b60c6_Screen-Shot-2020-09-08-at-4.42.03-PM.png?expiry=1602547200000&hmac=Op0bzkD649k9EDajNj7eAlthFR5vJ6ow-yg2Ri6wuMk)‌

The example above shows how you can make a prediction given your \lambdaλ dictionary. In this example the logpriorlogprior is 0 because we have the same amount of positive and negative documents \(i.e. \log 1 = 0log1=0\).

### Applications of Naive Bayes

There are many applications of naive Bayes including:

* Author identification
* Spam filtering
* Information retrieval
* Word disambiguation

This method is usually used as a simple baseline. It also really fast.

