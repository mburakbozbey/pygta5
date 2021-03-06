# A Deep Neural Network Plays Crew 2
 <p align="center"> 
    <img src="https://github.com/mburakbozbey/pycrew2_sentdex/blob/master/giphy.gif" alt="img">
 </p>
 
- Adapted and inspired by sentdex’s Python Plays GTA V series.
- Sentdex <a href="https://github.com/Sentdex/pygta5" target="_blank">Github</a>
- Sentdex <a href="https://www.youtube.com/watch?v=ks4MPfMq8aQ&list=PLQVvvaa0QuDeETZEOy4VdocT7TOjfSA8a" target="_blank">Youtube</a>
### Objective

- Since Crew 2 game has a relatively big map which takes approximately 1 hour to drive across, a deep neural network model can be trained to drive as fast as possible by learning from front camera of the vehicle and pressed keys while playing.
- This is not a self-driving car application, the project's main objective is building & improving a real-time inference model on edge while driving with keyboard like an average player(me).  

### Dataset Description
- **Dataset Size:** 88 GB Training, (80%) & 22 GB Testing (20%) and ~10 GB Validation. Distribution of classes:

<p align="center"> 
 <img src="https://i.ibb.co/r5fhNpt/train.jpg" width="325"> <img src="https://i.ibb.co/HK7RvD1/Screenshot-1.jpgg" width="325">
</p>

- **Dataset Shape:** 180.800 training, 45.200 testing & 20.000 validation samples

### Demo Videos

<a href="https://www.youtube.com/watch?v=1Ho4b1gUS7Y" target="_blank">`First version`</a>

##### Training Details:
- **Dataset:** 40 GB Training (80%) & Testing (20%) and 10 GB Validation.
- **Model Architecture:** DenseNet121 with fine-tuning on ImageNet weights.
- **Duration:** Approx. 10 Hours, 8 Epochs.

### Why the model was fine-tuned on ImageNet weights?

- From the paper “How transferable are features in deep neural networks?” by J. Yosinski et al., even big datasets can benefit from transfer learning which improves generalization. 
- <a href="https://drive.google.com/open?id=1aGBy7CWERduEW1YBL_-PaiB1SiXR_uRv" target="_blank">Presentation</a>
 of the review of the paper

## TODO:
- <del>There're 9 classes for each pressed key but these are not mutually exclusive. Convert the objective to multi-label multiclass classification problem.</del>
- Fix storage problems: https://github.com/mverleg/array_storage_benchmark
- <del>Shuffle big dataset</del>
- <del>Create a Keras data generator</del>
- <del>Optimize training time by using the<a href="http://digital-thinking.de/tensorflow-vs-keras-or-how-to-speed-up-your-training-for-image-data-sets-by-factor-10/" target="_blank">reference</a></del>
- <del>Use mixed precision for training</del>: cannot be used efficiently with GTX 1060 Max Q due to 7.0+ compute capability requirement
- <del>Preprocess all dataset before training:</del>

`%timeit preprocess_input(df_feature) >> 1.01 s ± 8.95 ms per loop (mean ± std. dev. of 7 runs, 1 loop each)`
- Optimize inference time, current: 50ms, target: 10 ms
- Optimize screen capturing
- Adapt post-processing to main objective
- Add object detection for crash prevention
