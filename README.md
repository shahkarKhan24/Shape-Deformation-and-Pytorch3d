<h2>Generating a 2D Dataset From a Target mesh<a href= "https://colab.research.google.com/github/shahkarKhan24/Shape-Deformation-and-Pytorch3d/blob/main/Code.ipynb">   <img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/></h2>

Implementing 3D deformation using 2D guidance

Introducing adversarial loss while mesh deformation with 2D images.

Introducing the attention layer into the discriminator model to get more accurate results. Self-attention mechanisms capture dependencies between pixels or regions, enabling the model to focus on relevant parts of the input.

Visualizing and analyzing the result of all the approaches while also evaluating their losses.
<h2>Dataset</h2>
To create a dataset we use pytorch3D, first, we load the target object which is a .obj file, which is then converted into vertices and meshes. we experimented with several shapes to deformed, but it should be noted that the more complex the shape is the more time it will take to deform during training
<div>
<img src="https://github.com/shahkarKhan24/Shape-Deformation-and-Pytorch3d/blob/main/Images/dataset%20.png" width="400" alt="Dataset"/>
</div>


<h2>First Approach</h2>
First, we tried to use a simple 2D-3D approach, where we fed our 2D data which are silhouette images of our target mesh from different angles and faces. After feeding that into our training model we try to deform our source mesh into our desired target mesh by learning the deform vertices of our source mesh. We had to train for almost 2000 iterations to get the desired deformed target mesh.
<div>
<img src="https://github.com/shahkarKhan24/Shape-Deformation-and-Pytorch3d/blob/main/Images/Aproach%201.png" width="400" alt="A1"/>
</div>


<h2>Second Approach</h2>
The second method we use where we try to introduce adversarial loss into our training loop to get a better result. For this purpose we need to design a separate discriminator type model and feed it the predicted 2D images of our source mesh as well as the 2D images of our target mesh. The final result from this approach was a bit fuzzy then the simple method we tried before but it was still acceptable given half the training time.
<div>
<img src="https://github.com/shahkarKhan24/Shape-Deformation-and-Pytorch3d/blob/main/Images/Aproach%202.png" width="400" alt="A2"/>
</div>


<h2>Third Approach</h2>
The other approach we tried is to introduce a self-attention layer into our discriminator model. The self-attention mechanism is a technique commonly used in deep learning models, particularly in natural language processing (NLP) and computer vision tasks. It allows the model to weigh the importance of different input elements when making predictions. In the context of images, self-attention mechanisms capture dependencies between pixels or regions, enabling the model to focus on relevant parts of the input. In the context of our discriminator, we can integrate self-attention to enable the model to focus on important features of the input image. Here we observe that the final result that is deformed source mesh is quite smooth and matching with the target mesh visually.
<div>
<img src="https://github.com/shahkarKhan24/Shape-Deformation-and-Pytorch3d/blob/main/Images/Aproach%203%20Discriminator%20network.png" width="400" alt="A3"/>
</div>

