# Repository description 
This repo contains Encoder-Generator model implementation and Optimized search task for Generator of GAN.
The code is done in Jupyter notebook with comments in Russian.

## Part 1
We train a convolutional generative model (using **DCGAN**) on digit images from the **MNIST** dataset. The generator **G** here synthesize random images of digits **x** from some input latent vector **h**, which is sampled from the normal distribution.

<p align="center">
  <img width="300" height="150" src="https://github.com/bcd8697/Encoder-Generator-and-Inv-GAN/blob/main/generator.png">
</p>

## Part 2
After it a procedure **E** for obtaining the latent vector **h** from the input image with the digit **x** is created (assuming the previously obtained fixed generator **G**).

<p align="center">
  <img width="300" height="150" src="https://github.com/bcd8697/Encoder-Generator-and-Inv-GAN/blob/main/encoder.png">
</p>

The vector **h** is such that when it is fed into the generator **G**, it will produce an image of the initially given digit **x**.

<p align="center">
  <img width="300" height="150" src="https://github.com/bcd8697/Encoder-Generator-and-Inv-GAN/blob/main/generator1.png">
</p>

For the second part, 2 approaches are proposed:

2.1 Through the creation of a universal Feed-Forward model **h = E(x)**

2.2 Through an optimization search for **h** given **x**.
Explanation: A function that takes **x** (an image of a digit from the **MNIST** dataset) as input and returns a vector **h** is created. The resulting vector **h** satisfies the following condition: if we feed **h** into the previously obtained (fixed) generator **G**, then we must get an image close to the original **x**. Inside the created function, the vector **h** is obtained using some optimization (iteration) process (the search process for **h** is run for each input **x**), and not using the Feed-Forward model, as in paragraph 2.1
