<h2>Generating a 2D Dataset From a Target mesh<a href= "https://colab.research.google.com/github/shahkarKhan24/Shape-Deformation-and-Pytorch3d/blob/main/Code.ipynb">   <img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/></h2>

Implementing 3D deformation using 2D guidance

Introducing adversarial loss while mesh deformation with 2D images.

Introducing the attention layer into the discriminator model to get more accurate results. Self-attention mechanisms capture dependencies between pixels or regions, enabling the model to focus on relevant parts of the input.

Visualizing and analyzing the result of all the approaches while also evaluating their losses.
<h2>Dataset</h2>
To create a dataset we use pytorch3D, first, we load the target object which is an .obj file, which is then converted into vertices and meshes. we experimented with several shapes to deformed, but it should be noted that the more complex the shape is the more time it will take to deform during training
<h2>First Approach</h2>
First, we tried to use a simple 2D-3D approach, where we fed our 2D data which are silhouette images of our target mesh from different angles and faces. After feeding that into our training model we try to deform our source mesh into our desired target mesh by learning the deform vertices of our source mesh. We had to train for almost 2000 iterations to get a desired deformed target mesh.
