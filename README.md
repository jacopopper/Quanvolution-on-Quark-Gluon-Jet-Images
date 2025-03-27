# Quanvolution for Quark/Gluon Jet Tagging

During my BSc thesis, I worked on **quantum convolution**, a fancy name for applying a k×k-qubit quantum circuit to an image via a sliding window as a convolution kernel. The goal is to reduce the complexity of the image while capturing its essential features. The original work I did was on medical imaging, but I thought, “Hey, why not apply it to HEP? I mean, a matrix is a matrix…,” and that’s what I’ve done.

The first problem was how to go from having a cloud of points to having a matrix of values (also called an image) without losing too much information about the jets. Initially, I tried selecting the min and max values of η and φ (my x and y axes) dynamically for each jet, splitting that rectangle into 32×32 bins, and simply counting how many particles fell into each bin to define pixel intensity. **Spoiler**: it didn’t work too well.

The second (and, luckily, final) implementation is not far from the first one. The only change is that each pixel’s intensity is given by the total transverse momentum pT of the particles that fall into that bin. Here are the 2D and 3D representations of a jet:  
[insert image]  
[insert image]

On these 2D images, I applied **quanvolution**, where each 2×2 patch is processed by the following small quantum circuit with random parameters:  
[insert image]

After the quantum layer, the image is fed into a simple CNN model to produce a final prediction of the jet’s nature.

The idea behind all of this, and what fascinates me the most, is that, by using quantum states to represent pixels, we may generate interactions and new states not replicable by classical computation, and thus possibly extract unique features with such kernels.

**Conclusion:**  
The quantum component was implemented using Pennylane, it's the library I know and like the most.
[insert image accuracy]  
[...comment on these results]
