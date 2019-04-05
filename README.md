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

### Evolution of RNNs
The **LSTM** cells was propsed in 1997 by **Sepp Hocreiter and Jurgen Schmidhuber**. The goal was to overcome **Vanishing Gradient Problem**.
It basically allows certain inputs to be latched or stored for long period of time without forgetting them as would be the case in RNNs. 

### LSTM
The major concept behind LSTM was the idea that some signals(state variables) can be **kept fixed by using gates** and **reintroduced or not at an appropriate time in the future**. By doing so arbitrary time intervals can be represented and **temporal dependencies** can be captured. The main idea is that LSTMs can decide which info to **forget**, which to **store** and **when to use it**.

In **RNN** memory comes in **merges with the current event** and output comes out **as the prediction what input is* and **also as the part of the input** for the next iteration of the neural network.

**LSTM** keeps track of **Long term memory** ehich comes in and comes out and also **Short term memory** which also comes in and comes out and in every stage the **long and short term memory get merged** and from there we get a new **Long term memory**, **Short term memory** and a **prediction**.

We have four major compnents in an **LSTM** cell:
* Long Term Memory
* Short Term Memory
* Event 
* Output

### Working of LSTM Cell
The **three peices(Event, Long & Short Term Memory)** of information goes inside the neuron and some math happens and we get new peices of information which are:
* Updated Long Term Memory
* Updated Short Term Memory
* Prediction

Zooming in a bit in the **architecture of LSTM cell**, it contains **four gates**:
1. Forget Gate
2. Remember Gate
3. Learn Gate
4. Use Gate

**Step 1:** **Long Term Memory** goes to the **Forget Gate** where it forgets all the info that it doesn't consider usefull.

**Step 2:** **Short Term Memory** and **Event** are joined together in the **Learn Gate**.

**Step 3:** Now the **Long Term Memory** that we haven't forgotten yet plus the new info that we learned at **Learn Gate** get joined at **Remember Gate**. This gate outputs the **Updated Long Term Memory.**

**Step 4**: The **Use Gate** takes the same input as **Remember Gate** and gives us new **Short Term Memory** and our    **Prediction/Output.**

So to summarize we can say, we have **LTM & STM** coming in. An **Event** is also coming in. **Output, Updated LTM & STM** are coming out which are then passed to next **LSTM cell** and so on and so forth.  

**LSTM cell** is more complex than a simple **RNN cell** as here we have to apply **Four Functions**, each for a **gate** that we discusse earilier.

### Working Of Gates
#### Learn Gate
**STM** and **Event** are comnied through a **Linear Function** which consists of **joining the vectors**, **multipling a matrix** and **adding a bias** and finally putting all these in **tanh(activation function)**. 

As we have discussed that we have to **ignore certain part**, to do so we multiple the above result with an **Ignore Factor(a vector)**. 

We use **previous info of STM & Event** to calculate Ignore Factor. For **Ignore Factor** we create a small NN whose inputs are **STM** and **EVENT**, will pass them through a **Linear Function** and pass that through the **sigmoid function**.

#### Forget Gate
Takes in **LTM** and decides what part to keep and what to forget. So **LTM** from time (t-1) comes in and gets multiplied by a **Forget Factor**.

To calculate **Forget Factor** we use **STM** and **Event** and follow the same process as we did for **Ignore Factor**.

#### Remember Gate
We take output coming from **Forget Gate & Lerarn Gate** and we simply **add** them.

#### Use Gate
We apply **tanh activation function** at the output of **Forget Gate** and **Sigmoid activation function** at **combined STM & Event** and as a final step we **multiple** these two to get **output**, which also works as **new STM**.   
