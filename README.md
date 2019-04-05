## Long-Short Term Memory(Wiki)

Long short-term memory (LSTM) is an artificial recurrent neural network (RNN) architecture used in the field of deep learning. Unlike standard feedforward neural networks, LSTM has feedback connections that make it a "general purpose computer" (that is, it can compute anything that a Turing machine can). It cannot only process single data points (such as images), but also entire sequences of data (such as speech or video). For example, LSTM is applicable to tasks such as unsegmented, connected handwriting recognition or speech recognition.

### Recurrent Neural Networks
Many of real life decision making involves **Temporal Dependencies** ie our current decision(in our case output) depends not only on current input but also past inputs. Lets consider a simple case where we want to decide menu for todays dinner, as I had pizza yesterday so I should prefer a salad(maybe) to maintain a helthy dite. Decisions like these require some kind of memory, one should remember what he/she ate yesterday and on the basis of that he/she can decide toadys menu.

Recurrent Neural Networks or RNN are basically similar to **Feed-Forward Networks with the addition of memory**. 
RNN's basically Artificial Neural Networks which can capture Temporal Dependencies(Dependencies over time).

### History Of RNN
Feed-Forward Networks were simlpy unable to capture **Temporal dependencies**. Modeling time based data is very critical in many real world situation since signals like speech have time varying properties. Biological neural networks themselves have recurrance so the idea of applying the same concept to ANN was born. 

The first attempt to do so was using **Time Delay Neural Network(TDNN, 1989)**

After that, Simple RNN's or Elman Networks(1990) 

After further work a phenomenon called THE **VANISHING GRADIENT PROBLEM** came into picture.

### Vanishing Gradient Problem
Vanishing Gradient Problem refers to geometrical decay in the contribution of information over time. So caputring info that occured 6-10 steps backward was not possible. Despite the advantage of the memory all these network had this major flaw(extent of backward steps they can remember).

**LSTM** was introduced to address this very problem of **Vanishing Gradient Decent**.

### Applications of RNN
* Speech Recognition: Siri, Google Assistant, Alexa
* Time Series Prediction: Netflix, Stock Price Movements(Quant Hedge Funds)
* NLP: Machine Translation, Google Analytics, Chatbots
* Gesture Recognition: Intel, Qualcomm

### Difference between RNN and FFNN
1. **Manner in which we define inputs and outputs:** Instead of traing with a single input single output at each time step we use sequences since previous inputs matter
2. **Memory Elements that RNN's keep:** Current inputs as well as activations of neurons serve as input to the next time step.
  
### Comparision between FFNN and RNN
In FFNN the output at anytime is a function of **current inputs and weights alone**. But in RNN our output at any time t is not only dependent on **current input and weights but also on previous inputs(input at time t-1, t-2...t-n)**.

In **FFNN** we use an activation function to obtain hidden layer, for that all we need are **inputs** and the **weight matrix** connecting the inputs to the hidden layer. In **RNN** we use an activation function but here the input to the activation function is now the sum of the **product of inputs and their corresponding weight matrix** and **the product of the previous activation values and thier coresspondig weight martix**.

The **LSTM** cells was propsed in 1997 Sepp Hocreiter and JUrgen Schmidhuber. The goal was to overcome **Vanishing Gradient Problem**.
It basically allows certain inputs to be latched or stored for long period of time without forgetting them as would be the case in RNNs. 

### LSTM
The major concept behind LSTM was the idea that some signals(state variables) can be **kept fixed by using gates** and **reintroduced or not at an appropriate time in the future**. By doing so arbitrary time intervals can be represented and **temporal dependencies** can be captured. The main idea is that LSTMs can decide which info to **forget**, which to **store** and **when to use it**.



### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/heisenbuug/Testing/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://help.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.
