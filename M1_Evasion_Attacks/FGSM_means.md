**FGSM** stands for **Fast Gradient Sign Method**.

It is one of the most famous and efficient algorithms used to create "adversarial examples"—images that look normal to humans but trick computer vision models into making wrong predictions.

Here is the breakdown of how it works, using the concepts from your course script.

### 1. The Core Concept: "Gradient Ascent"
To **train** a model, we use *Gradient Descent*. We ask: "How should I change the model's weights to **reduce** error?"

To **attack** a model using FGSM, we do the opposite. We use *Gradient Ascent*. We ask: "How should I change the pixels of this image to **increase** error?"



### 2. The "Fast" & "Sign" Parts
* **Fast:** Unlike other attacks that might run complex optimizations for hours, FGSM is calculated in a single step. It is extremely computationally cheap.
* **Sign:** It doesn't care about the *amount* of the gradient, only the *direction* (positive or negative).
    * If a pixel's gradient is positive, FGSM adds a tiny bit of noise.
    * If a pixel's gradient is negative, FGSM subtracts a tiny bit of noise.

### 3. The Formula
This is the math line you used in your code earlier:

$$x_{adv} = x + \epsilon \cdot \text{sign}(\nabla_x J(\theta, x, y))$$

* **$x$:** The original clean image (e.g., a stop sign).
* **$\nabla_x J$:** The calculated gradient (the direction that increases error).
* **$\epsilon$ (Epsilon):** The "volume knob." A small number (like 0.01) that ensures the noise is too small for humans to notice, but enough to fool the math inside the neural network.

### Why it matters for your course
FGSM is the "Hello World" of AI attacks. It proves that you don't need complex tools to break a state-of-the-art system; you just need to know the math behind how the model "sees."

**Next Step:** Would you like me to explain the **"Epsilon"** parameter in more detail, perhaps with an analogy you can use in your video script?
