# Gated Recurrent Unit
A Gated Recurrent Unit (GRU) is a type of recurrent neural network (RNN) that is designed to handle sequential data. It is similar to a Long Short-Term Memory (LSTM) network, but it has fewer parameters, making it computationally less expensive.

## How GRUs work

GRUs use a gating mechanism to control the flow of information through the network. This mechanism consists of two gates:

*   **Update gate:** The update gate determines how much of the previous hidden state should be carried over to the current hidden state.
*   **Reset gate:** The reset gate determines how much of the previous hidden state should be forgotten.

These gates are implemented using sigmoid functions, which output values between 0 and 1. A value of 0 means that the gate is closed, and a value of 1 means that the gate is open.

The hidden state of a GRU is updated as follows:

$$h_t = (1 - z_t) \odot h_{t-1} + z_t \odot \tilde{h}_t$$

where:

*   $h_t$ is the current hidden state
*   $z_t$ is the update gate
*   $h_{t-1}$ is the previous hidden state
*   $\tilde{h}_t$ is the candidate hidden state

The candidate hidden state is calculated as follows:

$$\tilde{h}_t = \tanh(W_h x_t + U_h (r_t \odot h_{t-1}))$$

where:

*   $x_t$ is the current input
*   $W_h$ is the weight matrix for the input
*   $U_h$ is the weight matrix for the recurrent connection
*   $r_t$ is the reset gate

## Advantages of GRUs

*   **Reduced complexity:** GRUs have fewer parameters than LSTMs, making them computationally less expensive and faster to train.
*   **Good performance:** GRUs can achieve comparable performance to LSTMs on a variety of tasks.
*   **Easier to understand:** The simpler architecture of GRUs can make them easier to interpret and debug.

## Disadvantages of GRUs

*   **Less expressive:** In some complex tasks, LSTMs might offer more expressive power due to their additional gate.
*   **Vanishing/exploding gradients:** While GRUs mitigate the vanishing gradient problem, they can still be susceptible to it in very deep networks.
