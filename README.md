An independent project for learning and experience out of academic studies in which I implemented a transformer model using the petorch library to build a chatbot

# dataset
In the first step, I took data from the kaggle ( https://www.kaggle.com/datasets/grafstor/simple-dialogs-for-chatbot) site which included two files, where the first was arrays with serial numbers that described a sequence of calls and the second was the sentence that each serial number describes During the data processing process, I mapped parts that are not useful in the string and prepared it for the embedding stage

# model
During the model building phase, by using techniques from the OOP world, I created objects with the aim of realizing the following architecture:

![transformer_architecture](https://user-images.githubusercontent.com/96596252/189915591-6cf9c93a-62d7-48af-9fb7-d4369b1d6cbb.jpg)

When the guiding article was [[NIPS-2017-attention-is-all-you-need-Paper]](https://proceedings.neurips.cc/paper/2017/file/3f5ee243547dee91fbd053c1c4a845aa-Paper.pdf) from which the hyperampmeters were also taken 

The choice of the model was due to educational reasons and due to suitability for the task: 

* In the study pan, this model included a number of points from different models such as the ResNet model in the decoder and encoder stages and of course FC in the feed forward stages Something that gave experience and understanding in the implementation of a variety of pitches in the various models.
Moreover, the world of transformers is moving towards a revolution in the world of artificial intelligence and it was important for me to experiment with a model that is considered current (2022)
* In terms of adaptation to the task,It was clear that the model I would need for the task was from the RNN family. Transforner model could perform the NLP task with a high probability of success due to its many advantages such as the non-dependence during the training between the words, which could prevent the problem of the gradient vanishing during the training

In the particular case of the chatbot task - if we look at the data we can see that some sentences include quite a few words such as "Thank God! If I had to hear one more story about your coiffure..." when my hypothesis (not verified) was that in a model based on LSTM I would have more difficulty in the optimization stages and thus even poor performance

Inside the notebook you can see short explanations and formulas implemented at each stage according to the architecture on which the transformer is based

# Traning
In the training phase, as mentioned above, the selection of the hyperparameters was carried out according to the article's 
recommendation, except for the amount of layers that I had to reduce to 1 dSince I wanted to get a better intuition about the result obtained in the base state (num_layer =1)
In addition to runtime considerations that became long with the amount of layers - the conscious training was carried out using google colab pro

During the evaluation phase, it was possible to notice that the chatbot recognizes basic sentences and gives fairly short answers

Since my evaluation index at the moment relied only on the loss, looking at the following graph you can see that although the general trend is a downward trend, there is a fairly long shuffling between 4.4 - 4.2, so the amount of the epoch was not the one that created the problem, since the model had difficulty going down to a loss lower than 4.2

In the following graph you can see the average loss at the end of each epoch (at the beginning of epoch 0 the loss was 8.647)

<img width="633" alt="צילום מסך 2022-09-14 ב-12 51 17" src="https://user-images.githubusercontent.com/96596252/190125177-04f53d20-98c0-4de1-a7ab-8e52de0b5a76.png">

I hypothesized that the problem was the number of layers given to the model since, as mentioned above, the initial number of layers was 1 and the time was that the model was unable to create a correlation between sentences of a longer and more complicated magnitude as a result

I now trained the model with 6 hidden layers when I got a better intuition and inference of what was going on The result was surprising:

- In terms of the loss index, the situation remained almost unchanged and it was difficult to drop further from 4.2:

<img width="657" alt="צילום מסך 2022-09-17 ב-13 59 34" src="https://user-images.githubusercontent.com/96596252/190853341-79af4ae5-9130-4ce6-bef3-a62be3abd4f8.png">

- At the actual performance level of the chatbot, I discovered that the chatbot does not know how to answer even basic questions like "Hello" or "How are you" when with one layer it did succeed
After checking in various sources, I was relieved to find out that **there is a certain N where N represents the number of layers for which the actual performance of the model decreases** I also understood that this situation can be accepted **because the amount of data does not increase in a limit to the number of layers**

I trained the model for each of the values N = {1,2,3,4,5,6} in order to investigate the matter and find an optimal N for the problem


