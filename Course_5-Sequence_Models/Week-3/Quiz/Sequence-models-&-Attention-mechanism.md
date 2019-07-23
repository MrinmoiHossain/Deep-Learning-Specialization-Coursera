#### 1. Consider using this encoder-decoder model for machine translation.
<img src="https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/qXy2GwVdEeirxApwydYI3g_563d74fd24e481f841070e81da7ee0aa_Screen-Shot-2018-01-29-at-5.33.03-PM.png?expiry=1563926400000&amp;hmac=gAJ7haoPeMmQqxo-xJJBXYnWbbcvQlUijFdca4zbW9s" alt="" >
#### This model is a “conditional language model” in the sense that the encoder portion (shown in green) is modeling the probability of the input sentence xxx
##### Ans: False
#### 2. In beam search, if you increase the beam width BBB, which of the following would you expect to be true? Check all that apply.
##### Ans: 
- Beam search will run more slowly.
- Beam search will use up more memory.
- Beam search will generally find better solutions (i.e. do a better job maximizing ```P(y|x)```)
#### 3. In machine translation, if we carry out beam search without using sentence normalization, the algorithm will tend to output overly short translations. 
##### Ans: True
#### 4. Suppose you are building a speech recognition system, which uses an RNN model to map from audio clip xto a text transcript y. Your algorithm uses beam search to try to find the value of yyy that maximizes ```P(y|x)```.

#### On a dev set example, given an input audio clip, your algorithm outputs the transcript y^= “I’m building an A Eye system in Silly con Valley.”, whereas a human gives a much superior transcript y*= “I’m building an AI system in Silicon Valley.”
#### According to your model,
```
P(y{^}|x)=1.09*10^-7

P(y^*|x)=7.21*10^-8
```
#### Would you expect increasing the beam width B to help correct this example?
##### Ans: No, because P(y^*|x) \lessThanAndEqual P(y{^}|x) indicates the error should be attributed to the RNN rather than to the search algorithm.
#### 5. Continuing the example from Q4, suppose you work on your algorithm for a few more weeks, and now find that for the vast majority of examples on which your algorithm makes a mistake, P(y^*|x) > P(y{^}|x). This suggest you should focus your attention on improving the search algorithm.
##### Ans: True.
#### 6. Consider the attention model for machine translation.
<img src="https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/ZdQLWgVeEei_ZQ6W1G11dA_5ea60f98993ef910d93aaf10c16c4cc9_Screen-Shot-2018-01-29-at-5.38.58-PM.png?expiry=1563926400000&amp;hmac=JVi5YxIgx3eBmorgo1QECAlAHFOXwlUMqgzgPI9JqnA" alt="">
#### Further, here is the formula for ```\alpha<t,t'>```.
<img src="https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/kBdw_AVeEeiIOArs7r1YtA_da38112b640e4901fbbf692a9e6611be_Screen-Shot-2018-01-29-at-5.39.03-PM.png?expiry=1563926400000&amp;hmac=EEG6vOweWSO-y3oDJ_Kbf508nZqICbAyXkL6N8chbJQ" alt="" >
#### Which of the following statements about ```\alpha<t,t'>``` are true? Check all that apply.
##### Ans: 
- We expect ```\alpha<t,t'>``` to be generally larger for values of ```\alpha<t'>``` that are highly relevant to the value the network should output for ```y^{<t>}```. (Note the indices in the superscripts.)
- ```\sum(t', \alpha<t,t'>) = 1 (Note the summation is over t'.)
#### 7. The network learns where to “pay attention” by learning the values ```e^{<t,t’>}```, which are computed using a small neural network:
#### We can't replace ```s^{<t-1>}``` with ```s^{<t>}``` as an input to this neural network. This is because ```s^{<t>}``` depends on ```a^{<t,t’>}``` which in turn depends on ```e^{<t,t’>}```; so at the time we need to evalute this network, we haven’t computed ```s^{<t>}``` yet.
##### Ans: True
#### 8. Compared to the encoder-decoder model shown in Question 1 of this quiz (which does not use an attention mechanism), we expect the attention model to have the greatest advantage when:
##### Ans: The input sequence length ```T_x``` is large. 
#### 9. Under the CTC model, identical repeated characters not separated by the “blank” character (_) are collapsed. Under the CTC model, what does the following string collapse to?
```__c_oo_o_kk___b_ooooo__oo__kkk```
##### Ans: cookbook
#### 10. In trigger word detection, ```x^{<t>}``` is:
##### Ans: Features of the audio (such as spectrogram features) at time t.