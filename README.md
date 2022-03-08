# targeted-absa
Targeted Aspect Based Sentiment Analysis

Four aspects were considered: ['general','price','safety','transit-location']
Model summary:

```Model: "model_1"
__________________________________________________________________________________________________
 Layer (type)                   Output Shape         Param #     Connected to                     
==================================================================================================
 input_ids (InputLayer)         [(None, 26)]         0           []                               
                                                                                                  
 attention_mask (InputLayer)    [(None, 26)]         0           []                               
                                                                                                  
 tf_bert_model_1 (TFBertModel)  TFBaseModelOutputWi  109482240   ['input_ids[0][0]',              
                                thPoolingAndCrossAt               'attention_mask[0][0]']         
                                tentions(last_hidde                                               
                                n_state=(None, 26,                                                
                                768),                                                             
                                 pooler_output=(Non                                               
                                e, 768),                                                          
                                 past_key_values=No                                               
                                ne, hidden_states=N                                               
                                one, attentions=Non                                               
                                e, cross_attentions                                               
                                =None)                                                            
                                                                                                  
 global_average_pooling1d_1 (Gl  (None, 768)         0           ['tf_bert_model_1[0][0]']        
 obalAveragePooling1D)                                                                            
                                                                                                  
 dropout_76 (Dropout)           (None, 768)          0           ['global_average_pooling1d_1[0][0
                                                                 ]']                              
                                                                                                  
 dense_1 (Dense)                (None, 128)          98432       ['dropout_76[0][0]']             
                                                                                                  
 dropout_77 (Dropout)           (None, 128)          0           ['dense_1[0][0]']                
                                                                                                  
 output_general (Dense)         (None, 3)            387         ['dropout_77[0][0]']             
                                                                                                  
 output_price (Dense)           (None, 3)            387         ['dropout_77[0][0]']             
                                                                                                  
 output_safety (Dense)          (None, 3)            387         ['dropout_77[0][0]']             
                                                                                                  
 output_transit (Dense)         (None, 3)            387         ['dropout_77[0][0]']             
                                                                                                  
==================================================================================================
Total params: 109,582,220
Trainable params: 109,582,220
Non-trainable params: 0
__________________________________________________________________________________________________
```

![model_architecture](https://github.com/harshita219/targeted-absa/blob/main/model.png)

### Results

1. For Location-1, performance of BERT for detecting 3 sentiments for each aspect: ['Negative','None','Positive']

  * general_f1_score: 0.0.7385 - general_acc: 0.8384 
  
  * price_f1_score: 0.8202 - price_acc: 0.9497 
  
  * safety_f1_score: 0.8236 - safety_acc: 0.9651 
  
  * transit_f1_score: 0.6037 - transit_acc: 0.9188


2. For Location-2, performance of BERT for detecting 3 sentiments for each aspect: ['Negative','None','Positive']

  * general_f1_score: 0.6102 - general_acc: 0.8119 
  
  * price_f1_score: 0.6802 - price_acc: 0.9098 
  
  * safety_f1_score: 0.5904 - safety_acc: 0.9381 
  
  * transit_f1_score: 0.4803 - transit_acc: 0.9098
  
  
#### => Failure Analysis [incoming]


### References:
https://keras.io/examples/nlp/text_classification_with_transformer/

SentiHood: Targeted Aspect Based Sentiment Analysis Dataset for Urban Neighbourhoods (COLING 2016)

Context-Guided BERT for Targeted Aspect-Based Sentiment Analysis (AAAI 2021)

Utilizing BERT for Aspect-Based Sentiment Analysis via Constructing Auxiliary Sentence (ACL 2019)
