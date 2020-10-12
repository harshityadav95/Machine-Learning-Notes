# Laplace Smoothing

### Laplacian Smoothing

![](.gitbook/assets/image%20%2815%29.png)

### Log Likelihood, Part 1

To compute the log likelihood, we need to get the ratios and use them to compute a score that will allow us to decide whether a tweet is positive or negative. The higher the ratio, the more positive the word is:![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/jRdwvis8SNCXcL4rPMjQlg_d8b30951c82b4b9f8f20b8f0e56d0a83_Screen-Shot-2020-09-08-at-4.01.25-PM.png?expiry=1602547200000&hmac=E02nZ-tlIh4eN9vI98nZ-jA9gICUQYH_q15qVzIkWJg)

![](.gitbook/assets/image%20%2818%29.png)

![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/I1jOUPkpSRmYzlD5KSkZUg_8d00fbc64ac94b9a9d9c41d367288447_Screen-Shot-2020-09-08-at-4.10.13-PM.png?expiry=1602547200000&hmac=qIUvVakg2SjnGDIU__zNIclelY8W8B6R9V1fP0Hzg6w)

Having the \lambdaλ dictionary will help a lot when doing inference.

### Log Likelihood Part 2

Once you computed the \lambdaλ dictionary, it becomes straightforward to do inference:![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/lqWbkNaCS5alm5DWgvuWoQ_2d4cdfc82bf142f08b89cb49f2908ef8_Screen-Shot-2020-09-08-at-4.17.43-PM.png?expiry=1602547200000&hmac=64kQox2rzZ13upN-wHXyyLD6jDokrCUbYQj2i3G6cXg)

As you can see above, since 3.3 &gt; 03.3&gt;0 , we will classify the document to be positive. If we got a negative number we would have classified it to the negative class.

![](.gitbook/assets/image%20%281%29.png)

### Testing naïve Bayes

![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/DBzYqctbQdSc2KnLW5HURA_3de7717134ec4f3ea36f9318083b60c6_Screen-Shot-2020-09-08-at-4.42.03-PM.png?expiry=1602547200000&hmac=Op0bzkD649k9EDajNj7eAlthFR5vJ6ow-yg2Ri6wuMk)

The example above shows how you can make a prediction given your \lambdaλ dictionary. In this example the logpriorlogprior is 0 because we have the same amount of positive and negative documents \(i.e. \log 1 = 0log1=0\).

