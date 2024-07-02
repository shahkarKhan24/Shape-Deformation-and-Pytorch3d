<h2>Shape Deformation Using 2D Guidance<a href= "https://colab.research.google.com/github/shahkarKhan24/Shape-Deformation-and-Pytorch3d/blob/main/Code.ipynb">   <img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/></h2>
  
-Generating 2D Dataset.
-Implementing 3D deformation using 2D guidance.
-Introducing adversarial loss while mesh deformation with 2D images.
-Introducing the attention layer into the discriminator model to get more accurate results. Self-attention mechanisms capture dependencies between pixels or regions, enabling the model to focus on relevant parts of the input.
-Visualizing and analyzing the result of all the approaches while also evaluating their losses.

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

<h2>Training</h2>
To analyze our approaches we were mainly focused on the visual result rather than the losses, but still we were keeping track of the all the losses to be as low as possible specially in first approach.
<h5>Approach 1</h5>
In the first approach, which was without adversarial loss, we train our model for up to 2000 iteration which WAS more than enough to get our desired shape in smooth and efficient way. In later figure  you can see the source mesh being gradually deform into target mesh over the course of 2000 iteration. We also visualize the mesh in the for of point clouds to get better visual understanding
<div>
<img src="https://github.com/shahkarKhan24/Shape-Deformation-and-Pytorch3d/blob/main/Images/training%20A1.png" width="500" alt="TRAINING A1"/>
  <img src="https://github.com/shahkarKhan24/Shape-Deformation-and-Pytorch3d/blob/main/Images/Losses.png" width="400" alt="Losses A1"/>
</div>
<h5>Approach 2</h5>
The training take longer time in this method then the previous one, so we run our training loop for only 1000 iteration. Which is half as much we did in earlier approach. The visual result were a little fuzzy and rough but given that we train it for only 1000 iteration the result was quite acceptable

<div>
<img src="https://github.com/shahkarKhan24/Shape-Deformation-and-Pytorch3d/blob/main/Images/training%20A2.png" width="500" alt="TRAINING A2"/>
  <img src="https://github.com/shahkarKhan24/Shape-Deformation-and-Pytorch3d/blob/main/Images/Aproach%202%20losses.png" width="400" alt="Losses A2"/>
</div>

<h5>Approach 3</h5>
We train this network also for 1000 iteration and the visual result were quite satisfactory you can observe the final result in below figures and comparison between the simple discriminator network and the complex one. You can clearly see the difference in result in mention figures 10 for the simple discriminator network and the one with self-attention mechanism
<div>
<img src="https://github.com/shahkarKhan24/Shape-Deformation-and-Pytorch3d/blob/main/Images/A2%20and%20A3%20compare.png" width="300" alt="TRAINING A3"/>
</div>



