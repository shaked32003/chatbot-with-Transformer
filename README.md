An independent project for learning and experience out of academic studies in which I implemented a transformer model using the petorch library to build a chatbot

The main goals of the project were not to achieve high accuracy but to experiment with PyTorch and building a deep neural network by implementation of the architecture of the transformer model as well as to work with a database not preloaded by PyTorch

In the first step, I took data from the kaggle ( https://www.kaggle.com/datasets/grafstor/simple-dialogs-for-chatbot) site which included two files, where the first was arrays with serial numbers that described a sequence of calls and the second was the sentence that each serial number describes During the data processing process, I mapped parts that are not useful in the string and prepared it for the embedding stage

During the model building phase, by using techniques from the OOP world, I created objects with the aim of realizing the following architecture:

![transformer_architecture](https://user-images.githubusercontent.com/96596252/189915591-6cf9c93a-62d7-48af-9fb7-d4369b1d6cbb.jpg)

When the guiding article was [[NIPS-2017-attention-is-all-you-need-Paper]](https://proceedings.neurips.cc/paper/2017/file/3f5ee243547dee91fbd053c1c4a845aa-Paper.pdf) from which the hyperampmeters were also taken 

after I studied the mathematical pan of the model The choice of the model was due to educational reasons and due to suitability for the task: 

* In the study pan, this model included a number of points from different models such as the ResNet model in the decoder and encoder stages and of course FC in the feed forward stages Something that gave experience and understanding in the implementation of a variety of pitches in the various models
* In terms of adaptation to the task,It was clear that the model I would need for the task was from the RNN family. Transforner model could perform the NLP task with a high probability of success due to its many advantages such as the non-dependence during the training between the words, which could prevent the problem of the gradient vanishing during the training

In the particular case of the chatbot task - if we look at the data we can see that some sentences include quite a few words such as "Thank God! If I had to hear one more story about your coiffure..." when my hypothesis (not verified) was that in a model based on LSTM I would have more difficulty in the optimization stages and thus even poor performance

Inside the notebook you can see short explanations and formulas implemented at each stage according to the architecture on which the transformer is based

In the training phase, as mentioned above, the selection of the hyperparameters was carried out according to the article's 
recommendation, except for the amount of layers that I had to reduce to 1 due to the inability to train with the existing hardware - the conscious training was carried out using google colab pro


