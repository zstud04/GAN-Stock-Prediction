## LSTM Background
LSTM (Long short-term memory) is a specific kind of RNN.

### Key attributes of RNN(Recurrent Neural Networks)
- Uses sequential/time data
- often used for ordinal problems(NLP, language, etc.)
- Used in google translate, etc.
- "MEMORY"
    - Use info from previous inputs to influence current input + output
        - Vs traditional neural networks where I/O is independent
- Look at the larger context for determining the meaning of each input/output
- Share parameters across layers of the network
    - Feedforward networks have different weights for each node, but RNNs share the same weight param for each layer
    - Weights are still adjusted with back-prop
        - back-prop works by calculating errors from output to input layer, and then adjusting the parameters to fit the model
- Two main issues:
    - concerning GRADIENT: slope of the loss function along the error curve.
    - Dissapearing gradients:
        - when gradient is too small and gets smaller, updating params until the weights become insignificant.
    - Exploding gradients:
        - gradient becomes too large, model weights grow too large
    - Solution is to reduce number of hidden layers in the NN

### Key attributes of LSTM
- LSTM doesn't have the same exploding/dissapearing gradient issue of a normal RNN
- Includes feedback connections
- Takes larger context into account

### Key attributes of GRU
- Gated Recurrent unit
- Kind of RNN
 - uses a gating mechanism to control flow of info between cells
- derived from LSTM
- also solves exploding/dissapearing gradient issue
- Update, reset gate decide what info should remain and be disposed of
- GRU has less parameters than LSTM
- Perform better than LSTM on smaller and less frequent datasets

### Key attributes of GAN
- Generative adversarial network
- based on zero-sum non-cooperative games
- TWO COMPONENTS:
    - Generator:
        - goal is to generate examples that can look as realistic as possible
    - Discriminator:
        - goal is to discriminate between real and fake generated examples
- Various new types of GANs
    - CGAN
        - Uses extra-label info to improve generator
    - Wasserstein GAN
        - includes Wasserstein distance to loss function
- In our project we want the GAN discriminator to maximize the probability of assigning the correct label to samples
    - Goal of generator is to minimize this function

#### WGAN-GP(Wasserstein GAN)
- basic GAN discriminator is slow, unstable
- WGAN-GP improves the training of GAN

##### Wasserstein Distance
- (Earth mover distance)
- "Minimum cost of transporting mass in converting the data distrubtion to the data distribution"
- Used to find distance between two probability distributions
- We are essentially transforming one pile of sand into another pile of sand, and find the optimal distance by measuring the amount of distance each sand grain is moved by the amount of sand it carries
- Outputs a scalar score, not a probability p
    - as opposed to GAN



 