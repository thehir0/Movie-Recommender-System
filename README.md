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

