# Lab Task - 2: Part-of-Speech Tagging, Chunking and Named Entity Recognition using CRF++

## LAYOUT OF THE PROJECT: 
  
  -> The project contains a root folder with the name *19074005-Dhruv-Gupta* which contains three 
     main-folders – 
  
  1) Chunking
  
  2) POS Tagging (Part-of-Speech Tagging)
  
  3) NER (Named Entity Recognition)
  
  -> Each main-folder individually contains- 
  
    => 3(three) sub-folders with the name of main-folder followed by an integer.
       For example – chunking_1, POS_tagging_1, NER_1, chunking_2, POS_tagging_2, NER_2, chunking_3, NER_3, POS_tagging_3 etc.
       
    => Training file.
    
    => Testing file.
    
    => Script file to find accuracy.
  
  Further each sub-folder contains 4 files –
  
    1) Template used
    
    2) Model trained
    
    3) Output or result file
    
    4) Accuracy file
    
 ## Training and Testing – 
 
  To train the model, run the following command in cmd/terminal –
  
    crf_learn.exe -c 4.0 “path of template” “path of training file” “model name”
    
  To test the model, run the following command in cmd/terminal –
  
    crf_test.exe -m “model name as formed above” “path of testing file” > “name of output file”
    
  To check the accuracy of the output –
  
    python3 “path of evaluating script file” < "path of output file" > “name of accuracy file”
    
## CHUNKING – 
  Chunking is a process of extracting phrases from unstructured text. Chunking works on top of POS tagging,
  it uses POS-tags as input and provides chunks as output. Chunking is very important when you want to extract information from text.
  
  ### Note – 
  
  The dataset is extracted from the provided CoNLL shared task 2000.
  
   ### Template 1:

    It is the default template as provided by the CoNLL shared task 2000.
    
   ### Template 2:
    
    Reduced the feature set of the default template keeping the window set same.
    
   ### Template 3:
    
    Reduces the window set by removing all the negative relative system coordinates and keeping only the positive ones 
    and some amount of feature set is also reduced.
    
   ### Accuracy – Its accuracy comes out to be around 94-96%.

  ## NER –
  Named entity recognition (NER) is a natural language processing (NLP) technique that automatically identifies 
  named entities in a text and classifies them into predefined categories. 
  Entities can be names of people, organizations, locations, times, quantities, monetary values, percentages, and more.

  ### Note – 
  
  The dataset is extracted from the provided CoNLL NER shared task 2003.
  
   ### Template 1:
    
    The feature set is decreased to some extent.
    
   ### Template 2:
    
    The feature set and window set are changed from both the sides i.e. the positive and negative extremes both.
    
   ### Template 3:
    
    The extreme positive window set range is reduced to decrease the overall range.
    
   ### Accuracy – Its accuracy comes out to be around 84-85%.
    
  ## POS Tagging – 
  It is a process of converting a sentence to forms – list of words, list of tuples (where each tuple is having a form (word, tag)). 
  The tag in case of is a part-of-speech tag, and signifies whether the word is a noun, adjective, verb, and so on.
  
  ### Note – 
  
  The dataset is extracted from the chunking dataset using the following command – 
        
       awk '(print $1, $2)' filename
                
    
   ### Template 1:
      
      The default template is used by reducing the column size by 1 as the training and testing files 
      of POS tagging contains one less column than the chunking part.
    
   ### Template 2:
      
      The feature set is reduced by keeping only some of the coordinates from both positive and negative parts.
    
   ### Template 3:
      
      The window set is changed with respect to the default template.
   
   ### Accuracy – Its accuracy comes out to be around 93-94%.

