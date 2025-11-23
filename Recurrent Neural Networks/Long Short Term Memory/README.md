# Long Short Term Memory
Long Short-Term Memory (LSTM) networks are a type of recurrent neural network (RNN) capable of learning order dependence in sequence prediction problems. They were introduced by Hochreiter & Schmidhuber (1997) to address the vanishing gradient problem that standard RNNs face when learning long-term dependencies.

## Key Concepts

*   **Recurrent Neural Networks (RNNs):** Neural networks designed to process sequential data, where the output at a given time step depends on the current input and the previous hidden state.
*   **Vanishing Gradient Problem:** In standard RNNs, gradients can shrink exponentially over long sequences, making it difficult to learn long-term dependencies.
*   **Exploding Gradient Problem:** Conversely, gradients can also grow exponentially, leading to unstable training.
*   **Gating Mechanism:** LSTMs introduce a sophisticated gating mechanism that allows them to selectively remember or forget information over long sequences.

## LSTM Architecture

An LSTM cell consists of the following main components:

1.  **Cell State (Ct):** The core memory of the LSTM. It runs straight through the entire chain, with only some minor linear interactions. Information can be added to or removed from the cell state via gates.
2.  **Input Gate (it):** Decides which new information from the current input and previous hidden state should be stored in the cell state.
    *   `it = σ(Wi * [ht-1, xt] + bi)`
    *   `C_candidate = tanh(Wc * [ht-1, xt] + bc)`
3.  **Forget Gate (ft):** Decides what information to throw away from the cell state.
    *   `ft = σ(Wf * [ht-1, xt] + bf)`
4.  **Output Gate (ot):** Decides what part of the cell state to output as the hidden state.
    *   `ot = σ(Wo * [ht-1, xt] + bo)`

## Equations

The operations within an LSTM cell at time `t` are typically defined as follows:

*   **Forget Gate:**
    `ft = σ(Wf * [ht-1, xt] + bf)`
    This gate determines what information from the previous cell state `Ct-1` should be forgotten. `σ` is the sigmoid activation function, which outputs values between 0 and 1.

*  **Input Gate:**
    `it = σ(Wi * [ht-1, xt] + bi)`
    This gate decides which new information to add to the cell state. The candidate values `C_candidate` are created using the tanh activation function:
    `C_candidate = tanh(Wc * [ht-1, xt] + bc)`

*  **Cell State Update:**
    The cell state is updated by combining the previous cell state and the new candidate values:
    `Ct = ft * Ct-1 + it * C_candidate`
*  **Output Gate:**
    `ot = σ(Wo * [ht-1, xt] + bo)`
    This gate determines what part of the cell state to output as the hidden state. The new hidden state `ht` is computed as:
    `ht = ot * tanh(Ct)`
*  **Hidden State:**
    The hidden state `ht` is the output of the LSTM cell at time `t`
    `ht = ot * tanh(Ct)`
    This state is used for predictions and is passed to the next time step.
