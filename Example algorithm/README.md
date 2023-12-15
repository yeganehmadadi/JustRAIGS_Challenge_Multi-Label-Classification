## JustRAIGS Example Algorithm

This is an example repository for making an algorithm submission for the [JustRAIGS challenge](https://justraigs.grand-challenge.org/). This algorithm is just for inference of your model.

You can upload your algorithms [here](https://justraigs.grand-challenge.org/). If you have a verified account on Grand Challenge and are accepted as a participant in the JustRAIGS challenge, you should be able to submit your Docker container. If something does not work for you, please do not hesitate to [contact us](mailto:yeganeh.madadi@gmail.com) or add a post to the [forum](https://justraigs.grand-challenge.org).

Here are some links that may also be useful:

* [Tutorial on how to make an algorithm container on Grand Challenge](https://grand-challenge.org/documentation/create-your-own-algorithm/)

* [Docker documentation](https://docs.docker.com/)

* [Evalutils documentation](https://evalutils.readthedocs.io/en/latest/)

* [Grand Challenge documentation](https://comic.github.io/grand-challenge.org/algorithms.html)


### Prerequisites

You will need to have [Docker](https://docs.docker.com/) installed on your system. We recommend using [WSL 2.0](https://learn.microsoft.com/en-us/windows/wsl/install) if you are on Windows to install Linux on Windows with WSL and install Docker there.


### Adapt the container to your algorithm

This codebase uses a not-so-smart algorithm that you may want to adapt to a smarter one that was training using the training data provided on the challenge web page. This section explains how to do that.

#### 1. Change the Dockerfile.

  * You may want to change ![FROM pytorch/pytorch] to another base image that already has some machine learning packages installed.
  * Install the required packages (see comment in Dockerfile for an example).
  * Copy additional files, such as model weights (see comment in Dockerfile for example).

#### 2. All the magic happens in inference.py, specifically in the predict function of the JustRAIGS_algorithm class in that file. This function reads a single image, processes it and outputs a dictionary with the four expected outputs. Replace the dummy code in this function with the code for your inference algorihm. You may also want to load your model weights etc. in the __init__ function and use them later in the predict function.

#### 3. Run test.sh (or test.bat if you are on Windows and not on WSL 2.0) to build the container. This will also build the container. The output of this script should end like this (probably with different values for the four model outputs):

#### 4. Run export.sh, which will produce JustRAIGS_algorithm.tar.gz. We will need this file later when uploading the algorithm to Grand Challenge.

#### 5. Make a new algorithm [here](https://justraigs.grand-challenge.org/evaluation/development-phase/submissions/create/). Fill in the fields as specified on the form. Some important fields are:

 * Viewer: Choose Viewer CIRRUS Core (Public).
 * Inputs: Choose Color Fundus Image (Image).
 * Outputs: Choose Multiple Referable Glaucoma Likelihood (Anything), Multiple Referable Glaucoma Binary Decisions (Anything), Multiple Ungradability Scores (Anything), Multiple Ungradability Binary Decisions (Anything).

#### 6. When you are done, click Save.

#### 7. On the page of your new algorithm, go to Containers in the menu on the left and click Upload a Container. Now upload your .tar.gz file produced in step 4. You could also not build the container yourself, but use a GitHub repo. Then you should click Link GitHub Repo instead. It will take some time before your Docker container is Ready. Do not proceed with the following steps, once this is the case.

#### 8. You can try out your algorithm when clicking Try-out Algorithm on the page of your algorithm, again in the left menu.

#### 9. Now, we will make a submission to one of the test phases. Go to the [JustRAIGS Challenge page](https://justraigs.grand-challenge.org/) and click Submit. Choose which phase you want to submit to and fill out the form. Under Algorithm, you choose the algorithm that you just created. Then hit Save. After the processing in the backend is done, your submission should pop up on the leaderboard.
