![Static Badge](https://img.shields.io/badge/LICENSE-MIT-green?link=https%3A%2F%2Fgithub.com%2FSpeedFireF%2FSMB%2Fblob%2Fmain%2FLICENSE)

<!-- PROJECT LOGO -->
<div align="center">

  <h1 align="center">Movie Recommender System</h3>

  <p align="center">
    Recommend movies to users based on their metadata and interactions.
      </p>
    <a href="https://github.com/othneildrew/Best-README-Template">
    <img src="https://movielens.org/images/movielens-logo-white.svg" alt="Logo" width="130" height=130">
  </a>
  </p>
        Innopolis University
      <br />
        <p align="center">
          Almaz Dautov, DS21-02, a.dautov@innopolis.university
      </p>
    <a href="https://docs.google.com/document/d/1EFDBDdnAJcoI6JsgsRwj984szpzCN-dmRWe94COfexE/edit?usp=sharing"><strong> Report»</strong></a>
    <br />
</div>


## About the project
Recommender systems play a crucial role in various domains, offering personalized suggestions to users based on their preferences, interests, and past behaviors. The goal is to develop a machine learning model that suggests movies to users, taking into account their metadata details and favorite movies. The MovieLens 100K dataset, comprising 100,000 ratings from 943 users on 1682 movies, will serve as the foundation for this task. The dataset provides user ratings, demographic information, and details about each movie.

## Model

### LightFM
[LightFM](https://github.com/lyst/lightfm) is a Python implementation of a number of popular recommendation algorithms for both implicit and explicit feedback.

It also makes it possible to incorporate both item and user metadata into the traditional matrix factorization algorithms. It represents each user and item as the sum of the latent representations of their features, thus allowing recommendations to generalise to new items (via item features) and to new users (via user features).

### Architecture

Let $U$ be the set of users and $I$ be the set of items, and each user can be described by a set of user features $f_{u} \subset F^{U}$ whilst each items can be described by item features $f_{i} \subset F^{I}$. Both $F^{U}$ and $F^{I}$ are all the features which fully describe all users and items. 

The LightFM model operates based binary feedbacks, the ratings will be normalised into two groups. The user-item interaction pairs $(u,i) \in U\times I$ are the union of positive (favourable reviews) $S^+$ and negative interactions (negative reviews) $S^-$ for explicit ratings. For implicit feedbacks, these can be the observed and not observed interactions respectively.

For each user and item feature, their embeddings are $e_{f}^{U}$ and $e_{f}^{I}$ respectively. Furthermore, each feature is also has a scalar bias term ($b_U^f$ for user and $b_I^f$ for item features). The embedding (latent representation) of user $u$ and item $i$ are the sum of its respective features’ latent vectors:

$$ 
q_{u} = \sum_{j \in f_{u}} e_{j}^{U}
$$

$$
p_{i} = \sum_{j \in f_{i}} e_{j}^{I}
$$

Similarly the biases for user $u$ and item $i$ are the sum of its respective bias vectors. These variables capture the variation in behaviour across users and items:

$$
b_{u} = \sum_{j \in f_{u}} b_{j}^{U}
$$

$$
b_{i} = \sum_{j \in f_{i}} b_{j}^{I}
$$

In LightFM, the representation for each user/item is a linear weighted sum of its feature vectors.

The prediction for user $u$ and item $i$ can be modelled as sigmoid of the dot product of user and item vectors, adjusted by its feature biases as follows:

$$
\hat{r}_{ui} = \sigma (q_{u} \cdot p_{i} + b_{u} + b_{i})
$$

As the LightFM is constructed to predict binary outcomes e.g. $S^+$ and $S^-$, the function $\sigma()$ is based on the [sigmoid function](https://mathworld.wolfram.com/SigmoidFunction.html). 

The LightFM algorithm estimates interaction latent vectors and bias for features. For model fitting, the cost function of the model consists of maximising the likelihood of data conditional on the parameters described above using stochastic gradient descent. The likelihood can be expressed as follows:

$$
L = \prod_{(u,i) \in S+}\hat{r}_{ui} \times \prod_{(u,i) \in S-}1 - \hat{r}_{ui}
$$

Note that if the feature latent vectors are not available, the algorithm will behaves like a [logistic matrix factorisation model](http://stanford.edu/~rezab/nips2014workshop/submits/logmat.pdf).[2]

