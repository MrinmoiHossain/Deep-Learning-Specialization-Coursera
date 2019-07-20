#### 1. Suppose your training examples are sentences (sequences of words). Which of the following refers to the j^{th} word in the i^{th} training example?
##### Ans: x(i)<j>
#### 2. Consider this RNN:
<img src="https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/WVhjoPCuEee5Rg5IFJ7l8g_a7b6030c6e5a53b431fee7aaabecd9bd_Screen-Shot-2018-01-03-at-5.48.26-PM.png?expiry=1563667200000&amp;hmac=XW3S4bmWLgGGFDfSUZKvNXHrNUdcPW_vfQhAsKO5MHw" alt="">
#### This specific type of architecture is appropriate when:
##### Ans: Tx=Ty
#### 3. To which of these tasks would you apply a many-to-one RNN architecture? (Check all that apply).
<img src="https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/K59CdPCvEee7LQrRPHr2wA_4549ad1b1b590371eb3502e158a02447_Screen-Shot-2018-01-03-at-5.54.27-PM.png?expiry=1563667200000&amp;hmac=Mj5uNo_no_zUOZltRr6PTHXFpRD46xEeD7OiBO_jcyE" alt="">
##### Ans: 
- Sentiment classification (input a piece of text and output a 0/1 to denote positive or negative sentiment)
- Gender recognition from speech (input an audio clip and output a label indicating the speaker’s gender) 
#### 4. You are training this RNN language model.
<img src="https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/cxeeLPCvEee7YRLKCWJ4hg_bca1b05c70eece156b470abb2d0f0cad_Screen-Shot-2018-01-03-at-5.56.30-PM.png?expiry=1563667200000&amp;hmac=8h5N-CfNaOQENDtMuc1qzIH4SgEHbZQUdhzVMjobdks" alt="">
#### At the t^{th} time step, what is the RNN doing? Choose the best answer. 
##### Ans: Estimating P(y<t>|y<1>,y<2>,…,y<t-1>)
#### 5. You have finished training a language model RNN and are using it to sample random sentences, as follows:
<img src="https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/zOkWE_CvEee5Rg5IFJ7l8g_f36533d67eb6590d5bcb7021d88493eb_Screen-Shot-2018-01-03-at-5.58.53-PM.png?expiry=1563667200000&amp;hmac=91lnrYdvrGrLaJqa7Z_MRkQmC0Q4DFXSz6a2h2psdEE" alt="">
#### What are you doing at each time step t?
##### Ans: (i) Use the probabilities output by the RNN to randomly sample a chosen word for that time-step as y^<t>. (ii) Then pass this selected word to the next time-step.
#### 6. You are training an RNN, and find that your weights and activations are all taking on the value of NaN (“Not a Number”). Which of these is the most likely cause of this problem?
##### Ans: Exploding gradient problem.
#### 7. Suppose you are training a LSTM. You have a 10000 word vocabulary, and are using an LSTM with 100-dimensional activations a^{<t>}. What is the dimension of Gu at each time step?
##### Ans: 100
#### 8. Here’re the update equations for the GRU.
<img src="https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/y-VsavCwEeeVOQpGYM3DAA_b10afdb5d35702d711338d5b72ce5be7_Screen-Shot-2018-01-03-at-6.05.56-PM.png?expiry=1563667200000&amp;hmac=Xpa3ImBx2wrYN90eXKfYufruC69Ip6ioyU2Dmn3gtMA" alt="">
#### Alice proposes to simplify the GRU by always removing the Gu. I.e., setting Gu = 1. Betty proposes to simplify the GRU by removing the Gr. I. e., setting Gr = 1 always. Which of these models is more likely to work without vanishing gradient problems even when trained on very long input sequences?
##### Ans: Betty’s model (removing Gr), because if Gu˜0 for a timestep, the gradient can propagate back through that timestep without much decay. 
#### 9. Here are the equations for the GRU and the LSTM:
<img src="https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/ZJgnEfCxEeeVOQpGYM3DAA_2552c64114ba9a4a065a54e8e4855b39_Screen-Shot-2018-01-03-at-6.10.24-PM.png?expiry=1563667200000&amp;hmac=JyMSeFSWATGTi1bphRP6JYpINKibTjrVTYk5bqIENiA" alt="">
#### From these, we can see that the Update Gate and Forget Gate in the LSTM play a role similar to _______ and ______ in the GRU. What should go in the the blanks?
##### Ans: Gu and 1-Gu
#### 10. You have a pet dog whose mood is heavily dependent on the current and past few days’ weather. You’ve collected data for the past 365 days on the weather, which you represent as a sequence as x<1>,…,x<365>. You’ve also collected data on your dog’s mood, which you represent as y<1>,…,y<365>. You’d like to build a model to map from x?yx \rightarrow yx?y. Should you use a Unidirectional RNN or Bidirectional RNN for this problem?
##### Ans: Unidirectional RNN, because the value of y<t>y^{<t>}y<t> depends only on x<1>,…,x<t>, but not on x<t+1>,…,x<365>