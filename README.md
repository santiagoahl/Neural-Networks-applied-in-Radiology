
<h1 align="center">
  <br>
  <a href="https://imagineteam.com/images/Blog/0e17febd522cd9389b04ce5c00f25aec_L.jpg" width="200"></a>
  <br>
    Neural networks: An application in radiology
  <br>
</h1>

<h4 align="center">Designing an deep learning algorithm in the <a href="https://www.v7labs.com/open-datasets/chestx-ray14" target="_blank">ChestX-ray14</a> dataset in <a href="https://julialang.org/" target="_blank">Julia</a>.</h4>

<p align="center">
  <a href='https://julialang.org/' target="_blank"><img alt='julia' src='https://img.shields.io/badge/Julia-100000?style=for-the-badge&logo=julia&logoColor=3F9B0B&labelColor=CA3435&color=9955BB'/></a>
  <a href='https://fluxml.ai/Flux.jl/stable/' target="_blank"><img alt='flux' src='https://img.shields.io/badge/Flux.ij-100000?style=for-the-badge&logo=flux&logoColor=3F9B0B&labelColor=CA3435&color=3F9B0B'/></a><a href='https://juliapackages.com/p/imageio' target="_blank"><img alt='imageio' src='https://img.shields.io/badge/Imageio.ij-100000?style=for-the-badge&logo=imageio&logoColor=3F9B0B&labelColor=CA3435&color=CA3435'/></a><a href='https://juliapackages.com/p/imageio' target="_blank"><img alt='MLdatasets' src='https://img.shields.io/badge/MLdatasets.ij-100000?style=for-the-badge&logo=MLdatasets&logoColor=3F9B0B&labelColor=CA3435&color=9955BB'/></a>
</p>

<p align="center">
  <a href="#model-overview">Model overview</a> •
  <a href="#how-to-use">How To Use</a> •
  <a href="#credits">Credits</a> •
</p>

![screenshot](https://assets-global.website-files.com/5d7b77b063a9066d83e1209c/61e9d024a8f37c0c35fc7aad_ChestX-ray14-0000001144-46559e6f_9iVbS0m.jpeg)

Note: We are currently optimizing the model. Building a deeper CNN arquitecture and cleaning better the data.

## Model overview

* **ChestX-ray14 Dataset** which consist on
    - A medical imaging dataset which comprises 112,120 frontal-view X-ray images.
    - 30,805 (collected from the year of 1992 to 2015) unique patient images.
    - Text-mined fourteen common disease labels, mined from the text radiological reports via NLP techniques.
    - Diseases: 
        - Atelectasis
        - Cardiomegaly
        - Effusion
        -Infiltration
        - Mass; 6, Nodule
        -Pneumonia; 8, Pneumothorax
        - Consolidation
        - Edema
        - Emphysema
        - Fibrosis
        - Pleural_Thickening
        - Hernia.
        
* **Diseases correlation**: The dataset documentation explains the correlation between those multiple diseases. Since we thought this model as a unique-label classificator, then we found an improvement opportunity for our model accuracy here.

![screenshot](https://winter-anchovy-50e.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F01873699-f86d-4d31-9366-b04c9c1a56fe%2FUntitled.png?table=block&id=31fbfd52-4042-4b48-8e14-903249e924b6&spaceId=12eea25e-0790-4a8f-aa1c-b60f93c02da2&width=1440&userId=&cache=v2)

* **Data set treatment**: Ordering the data and changing string labels to number labels (from 1 up to 14) and importing this with `DataFrame` julia package (which is analog with respect to pandas DataFrames).

![screenshot](https://winter-anchovy-50e.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Fcf268d3d-da51-4be2-ab10-a5e6248e6785%2FUntitled.png?table=block&id=27cd59b0-fc68-436f-b64a-d93a116ebc67&spaceId=12eea25e-0790-4a8f-aa1c-b60f93c02da2&width=1760&userId=&cache=v2)
  
* **Building the model** We dropped the whole dataset out into a training and testing sets and defined the dense neural network with its activation funtion `softmax` the loss function `cross-entropy` cause it is frequently used in category prediction and the optimizer `ADAM`. 
![screenshot](https://winter-anchovy-50e.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F9aafdcb1-a4cb-4e7b-97b5-3bfdb9c60b04%2FUntitled.png?table=block&id=635b1294-810b-465f-8bd8-64149920971d&spaceId=12eea25e-0790-4a8f-aa1c-b60f93c02da2&width=2000&userId=&cache=v2)

* **Training the model**: We trained the model with 1000 epochs
* **Learning curve**
![screenshot](https://winter-anchovy-50e.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Fcc41aec4-27a4-42d0-93fc-eab4d7846faf%2FUntitled.png?table=block&id=65b4ed23-6a12-48aa-83a6-9c3094e06212&spaceId=12eea25e-0790-4a8f-aa1c-b60f93c02da2&width=1800&userId=&cache=v2)

## How To Use

To clone and run this model, you'll need [Git](https://git-scm.com) and [Julia](https://julialang.org/downloads/) installed on your computer. From your command line:

```bash
# Clone this repository
$ https://github.com/santiagoahl/Neural-Networks-applied-in-Radiology.git

# Go into the repository
$ cd Neural-Networks-applied-in-Radiology

# Install Julia
$ cd ~/Downloads
$ wget https://julialang-s3.julialang.org/bin/linux/x64/1.8/julia-1.8.0-linux-x86_64.tar.gz
$ wget https://julialang-s3.julialang.org/bin/linux/x64/1.8/julia-1.8.0-linux-x86_64.tar.gz
$ sudo cp -r julia-1.8.0 /opt/
$ sudo ln -s /opt/julia-1.8.0/bin/julia /usr/local/bin/julia
$ julia

# Install julia packages
julia> using Pkg 
julia> Pkg.add("IJulia")
julia> import Flux, Plots, Images

#Open Jupyter notebooks

$ jupyter notebook
```


## Credits

This model uses the following open source packages:

- [Flux.ij](https://fluxml.ai/Flux.jl/stable/)
- [MLdatasetsij](https://img.shields.io/badge/MLdatasets.ij-100000?style=for-the-badge&logo=MLdatasets&logoColor=3F9B0B&labelColor=CA3435&color=9955BB)
- [Jupyter notebooks](https://jupyter.org/)
- [ChestX-ray14 Open dataset](https://www.v7labs.com/open-datasets/chestx-ray14)


##Licence

MIT

---

> Personal Page [https://santiagoal.super.site/](https://www.amitmerchant.com) &nbsp;&middot;&nbsp;
> GitHub [@santiagoahl]https://github.com/santiagoahl) &nbsp;&middot;&nbsp;
> Twitter [@sahumadaloz](https://twitter.com/sahumadaloz)

