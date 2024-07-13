# -Travel-Itineraries
Project: Using Machine Learning to Enhance Travel Routes

Project goal. The goal of my project is to optimize travel routes for a delivery vehicle by using machine learning model predictions. This is a two-component problem: first, I train a machine learning model on the data to predict how long it will take a delivery vehicle to go from point one point to another, and I feed these predictions into a genetic algorithm which decides which is the most time efficient visit order for a given set of points.

Here is an illustration of my pipeline: data -> machine learning -> optimization with genetic algorithm

![image](https://github.com/user-attachments/assets/23066670-2b3a-461a-8da1-78734b7ccf30)


Data and Features. New York City taxi data set was taken from here, with an additional New York City weather dataset obtained from Kaggle.

Models. After doing a quick baselining with a basic linear regression on the main dataset I realized that a far more complex model was needed. To this end, I selected an XGBoost model to accommodate for my complex numeric and categorical features. I also used a LightGBM model when adding weather data because this package can handle categorical data and runs faster, but I used this model mostly for experimentation with features and did not include in my final pipeline.

Optimization. For any given set of locations, these locations are fed to the machine learning model, which predicts how long it will take to travel between each two given points. Then the algorithm "evolves" to find the visit order which minimizes time spent in transit.

Results. The XGBoost model had an error of 4.8 minutes in estimating a single trip's duration for a motor vehicle. While this may seem acceptable for one trip, the error may get bigger the more locations are visited. The genetic algorithm itself is fairly straightforward, but it must be noted that every genetic algorithm gives an optimal approximation, but not the single best solution there is.

Acknowledgements. Big thanks to this notebook for providing the code for the genetic algorithm and making it accessible.
