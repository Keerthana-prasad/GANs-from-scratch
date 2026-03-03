# Understanding GANs
GAN from scratch by defining two separate neural networks — a Generator and a Discriminator — and then training them together in an adversarial loop.

The Generator code starts with a dense layer that expands a random noise vector, applies Batch Normalization and ReLU, reshapes it into a 3D tensor, and then uses multiple Conv2DTranspose (upsampling) layers to progressively generate a 28×28 image (e.g., MNIST). The final layer uses tanh activation to scale pixel values to 
−
1
,
1
−1,1.

The Discriminator code uses Conv2D layers with LeakyReLU and Dropout to downsample the input image and extract features, then flattens the result and passes it through a dense layer with sigmoid activation to output a probability (real vs fake).

During training, the loop:

Generates fake images from noise.

Trains the discriminator on real + fake images using binary cross-entropy loss.

Trains the generator using the discriminator’s feedback so it learns to fool it.

Repeats this process iteratively until the generated images look realistic.

Writing code? Meet Codex.
Pair with Codex in your terminal or IDE, free for a limited time in your ChatGPT plan.
Install Codex

