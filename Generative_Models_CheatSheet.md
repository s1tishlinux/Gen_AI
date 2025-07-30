# Generative Models Cheat Sheet (Autoencoders, VAEs, GANs, cGANs)

## 1. What is a Generative Model?
A generative model is a type of machine learning model that learns patterns from real data and then can create new data that looks similar to what it has seen before. These models are useful for generating images, sounds, text, and more.

---

## 2. Autoencoder (AE)
**Definition:**
An autoencoder is a neural network with two main parts:
- **Encoder:** Compresses the input data into a small code (bottleneck).
- **Decoder:** Reconstructs the input data from this code.

**Purpose:** The autoencoder learns to output data as close as possible to its input. It is mainly used for data compression, denoising, and anomaly detection.

**Diagram:**
```
[Input] → [Encoder] → [Code] → [Decoder] → [Reconstructed Output]
```

**Code Example:**
```python
from tensorflow import keras
# Assume encoder and decoder are keras.models.Sequential() objects
autoencoder = keras.models.Sequential([encoder, decoder])
autoencoder.compile(loss="mse", optimizer="adam")
autoencoder.fit(X_train, X_train, epochs=20)
```

---

## 3. Denoising Autoencoder
**Definition:**
A denoising autoencoder is trained to remove noise from input data. It receives a noisy input and learns to output the clean, original version of the data.

**Diagram:**
```
[Noisy Input] → [Encoder] → [Code] → [Decoder] → [Clean Output]
```

**Use Case:**
Used in image restoration, sound cleaning, and data cleaning tasks.

---

## 4. Variational Autoencoder (VAE)
**Definition:**
A variational autoencoder is a more advanced autoencoder that learns to generate new data by sampling from a distribution of compressed codes, rather than a single fixed code for each input.

- The encoder outputs two vectors: the mean and variance for each dimension of the code.
- The model then samples from these distributions to generate new codes.
- The decoder tries to reconstruct data from these random codes, allowing the VAE to generate new, similar examples.

**Diagram:**
```
[Input] → [Encoder] → [Mean/Var] → [Random Sampling] → [Decoder] → [Generated Output]
```

**Use Case:**
VAEs are used for generating new, creative data—like making new images similar to those in the training set.

---

## 5. Generative Adversarial Network (GAN)
**Definition:**
A GAN is made up of two neural networks:
- **Generator:** Tries to create fake data that looks real.
- **Discriminator:** Tries to distinguish between real and fake data.

The generator and discriminator are trained together in a “game,” each improving their skills over time. The goal is for the generator to produce data so realistic the discriminator cannot tell if it’s fake.

**Diagram:**
```
[Noise] → [Generator] → [Fake Data]
                        ↓
              [Discriminator]
              ↑         ↓
        [Real Data]  [Fake Data]
```

**Use Case:**
GANs are used to generate new images, create realistic fake faces, improve image resolution, and more.

---

## 6. Conditional GAN (cGAN)
**Definition:**
A conditional GAN extends the regular GAN by allowing both the generator and discriminator to receive extra information (labels) so the generator can produce specific types of data (e.g., images of dogs or cars on demand).

**Diagram:**
```
[Noise + Label] → [Generator] → [Fake Data of that Label]
                        ↓
             [Discriminator gets label too]
              ↑                  ↓
       [Real Data + Label]   [Fake Data + Label]
```

**Use Case:**
cGANs are used for controlled image generation (e.g., generating pictures of a particular digit, object, or person).

---

## 7. Training Tips & Common Issues

| Problem              | Fixes & Tips                                                 |
|----------------------|--------------------------------------------------------------|
| Mode collapse        | Add noise, use batch normalization, tune learning rates.      |
| Unstable training    | Use smaller learning rates, regularization, label smoothing.  |
| Discriminator too good| Slow down training, update generator more frequently.        |

---

## 8. Real-World Applications
- Remove noise from images or audio (denoising)
- Create high-resolution versions of blurry images (super-resolution)
- Data augmentation (creating extra training samples)
- Generate realistic fake images for media or research
- Detect anomalies or rare events in data

---

## 9. Summary Table

| Model    | Main Function           | Description                                            |
|----------|------------------------|--------------------------------------------------------|
| AE       | Copy/compress          | Learns to compress and reconstruct data.               |
| DAE      | Clean up data          | Removes noise from data during reconstruction.         |
| VAE      | Generate new data      | Can generate new, realistic data by sampling codes.    |
| GAN      | Realistic fake data    | Competes to generate data indistinguishable from real. |
| cGAN     | Controlled fake data   | Can generate fake data for specific categories/labels. |

---

## 10. Visual Gallery
```
Autoencoder:   [Input] → [Encoder] → [Code] → [Decoder] → [Output]
Denoising AE:  [Noisy Input] → [Encoder] → [Decoder] → [Clean Output]
VAE:           [Input] → [Encoder] → [Mean/Var] → [Sample] → [Decoder] → [New Output]
GAN:           [Noise] → [Generator] → [Fake] ↓→ [Discriminator] ← [Real]
cGAN:          [Noise+Label] → [Generator] → [Fake (label)] ↓→ [Discriminator (label)] ← [Real (label)]
```

---

## 11. Quick Self-Quiz
- What is the main job of an autoencoder?
- How is a VAE different from a regular autoencoder?
- What does the discriminator do in a GAN?
- How does a conditional GAN differ from a regular GAN?
- Name a real-world use for each type of generative model.

---

# End of Cheat Sheet
