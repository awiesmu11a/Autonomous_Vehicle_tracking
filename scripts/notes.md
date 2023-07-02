# TODO

* Try extracting more info from the data; from top of my head see if city could help (Not done yet)

# Ideas:

* Try to incorporate Kalman Filter; could work
* Is there any way where I can look through huge chunk of data in single plot:
    - Can plot the distribution of mutlitple cases
    - Can simply plot the trajectories and look through
* Try to use lane_norm

# Possible cases:
* Car standing still
* Car changing lanes
* Car taking turns
* Car moving straight

# MLP implementation:
* The problem boiled to extending various types of curves; Even the same nature of curves had different representation due to rotation and translation.
* The MLP did not support the degree of nonlinearity to generalise to these curves.
* The low train and validation loss is due to the fact that the data is normalized around zero;
So, even the large change in trajectory near origin gave small MSE.
(**THIS IS AN IMPORTANT PROBLEM NOT CONSTRAINED TO MLP**).
* Since, model is linear could not think of a way to lane coordinates directly.
* One last thing to try: Try training without normalizing.

# Analysis on the dataset:
* classify the dataset in each of the possible cases. (not yet figured)
* Using the velocity:
    - Can extract turn 
    - Can extract straight
    - Can extract stationary
    - What about changing lanes?
* Looks like oritation of the roads (but centered around zero).
* Still don't know what they are for. But size of the array size of lane coordinates
* When added corresponding norm with coordinate no noticeable difference observed in the plot.
* Can classify the distribution:
    - velocity near zero means stationary (or sum near zero)
    - make line segment of input and output; find angle between them for turns
    - when angle near zero means either changing lanes or straight
    - Try to use the lane norm to finally classify these twwo
    - try to extract lane norm using the trajectories (line segments) of input and output; and compare it to the lanes to figure out changing lanes or not (**NOT YET IMPLEMENTED**)
============================================================================================

# Report skeleton

## Abstract
Trajectory prediction of the vehicles is one of the major problems in the domain of autonomous navigation. The vehicles are identified from the data extracted using sensors like LiDAR, RGBD Stereo Camera which could be then transformed to a pose to be used for the task of trajectory prediction. This is an important problem for safe functioning of various agents simultaneously, along with safety of pedestrians. Not only should the results produced during this step be precise but also the corresponding controller should function with same level accuracy. We will focus on the prediction step in this paper. Over the past years various approaches and algorithm have been introduced to tackle this problem mainly along the lines of unsupervised learning. In this paper we will first introduce the problem and present an analysis on the dataset used for the said task. Moving on to discuss the details of the various algorithms experimented along with the implementation details. Finally, we will present the results produced. Since, this is a milestone report on the project, better results are expected to be presented in the final report by using the approaches whose overview are mentioned in the section future works.

## Task Description and Exploratory analysis