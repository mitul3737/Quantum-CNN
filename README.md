# Quantum-CNN
This is a Quantum Convolutional Neural Network 

## Work Credits / © Copyright

Feel free to mention this repository in your work and give a star to the project. 


### How to run it locally
Fork this repository and use the link  to clone in your laptop/pc: ``` https://github.com/<your_GitHubusernaame>/Quantum-CNN.git ```
Once it's forked, just go to the folders and run the ipynb files.

### 1. Description:

This is a quantum convolutional neural network with autoencoder and PCA used for dimension reduction.

### 2. Ansatzes used in Convolutional Layer and Pooling Layer

An ansatz is a structured quantum circuit with adjustable parameters (e.g., rotation angles) that define a family of quantum states. It is used to explore the solution space in optimization problems.

### Types of Ansätze:

i). Problem-Inspired Ansätze: Designed based on the problem's structure (e.g., UCCSD for quantum chemistry).

ii) Hardware-Efficient Ansätze: Built using gates native to a specific quantum processor (e.g., Rigetti’s or IBM’s gate sets).

iii) Layer-Based Ansätze (Alternating Operator Ansatz): Used in QAOA, where layers of mixing and problem Hamiltonians alternate.

iv) Random or Ad-Hoc Ansätze: Constructed heuristically for flexibility but may suffer from trainability issues.

Ansatzes used in this [paper](https://arxiv.org/abs/2108.00661)
![image](https://github.com/user-attachments/assets/ddc84a2f-4608-4715-a5f2-45a57529b28e)

The accuracy of a QCNN also depends on ansatzes. So, checking its [expressivity](https://github.com/mitul3737/Supreme-QCNN/tree/main/Expressivity) and [entangling capability](https://github.com/mitul3737/Supreme-QCNN/tree/main/Entangling_Capability) might help choose the perfect ansatz.


### 3. Encoding: 


Encoding refers to the process of mapping classical data (numbers, vectors, images, etc.) into quantum states that can be processed by a quantum computer. Since quantum algorithms operate on qubits, classical information must first be converted into a quantum-readable format. 
This step is crucial for quantum machine learning (QML), optimization, and simulation tasks. There are encoding techniques like Basis Encoding, Amplitude Encoding, Angle Encoding, Qubit Encoding, Hamiltonian Encoding etc.

Here, we have used Angular Hybrid Encoding and Amplitude Hybrid Encoding.

### 4. QCNN Structure:
QCNN Architecture used from this [paper](https://arxiv.org/abs/2108.00661)
![image](https://github.com/user-attachments/assets/0e59a17f-4985-40f4-b394-4d0b0799ba22)


Here, I have used 

```

Conv_Pooling_Layer_Ansatzs = [['U_SU4',"custom_Pooling1",'U_SU4','custom_Pooling4','U_SU4','Pooling_ansatz1']]

Conv_Pooling_Layer_Params = [[15,10,15,14,15,2]]

Encodings = ['resize256', 'pca8', 'autoencoder8'] # dimensionality reduction techniques

dataset = 'mnist'

classes = [0, 1]

binary = False

cost_fn = 'cross_entropy'

```

Meaning, I have used these ansatzes in my QCNN architecture.

![image](https://github.com/user-attachments/assets/b7f6c42b-cbb8-401c-b4df-2c5ea7ba19dc)

Here, U_SU4 has 15 parameters, custom_Pooling1 has 10 parameters, custom_Pooling4 has 14 parameters, and Pooling_ansatz1 has 2 parameters.

You may change the anstazes and then change the parameters (Conv_Pooling_Layer_Params) accordingly. Within the encoding array, we have dimensionality reduction techniques used in each iteration. 

Moreover, the dataset carries the dataset type (for image classification, we used 'mnist' or 'fashion mnist') or path (for audio classification, we referred to the Dataset/Mel_Spectrograms folder). Binary remains "False" for the "cross-entropy" cost function, whereas the binary value is "True" when using "MSE."
### 5. Cost functions: 

As cost functions, we have used MSE (Mean Squared Error) and cross-entropy. Mean Squared Error (MSE) and Cross-Entropy are two commonly used cost functions in machine learning and deep learning for training models. 
They measure the difference between predicted outputs and true labels, but they are suited for different types of problems.

### 6. Training and Test Dataset:

For the image classification, the Keras dataset has been used.

```

if dataset == 'fashion_mnist':

        (x_train, y_train), (x_test, y_test) = tf.keras.datasets.fashion_mnist.load_data()

elif dataset == 'mnist':

        (x_train, y_train), (x_test, y_test) = tf.keras.datasets.mnist.load_data()

```

### 7. Conclusion: 
The accuracy remains near 98% for the image dataset



