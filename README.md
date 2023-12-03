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

## Evaluation

| Model                | ROC AUC | Precision@10 | Recall@10 |
|----------------------|---------|--------------|-----------|
| lightFM with FE*     | 0.7907  | 0.0364       | 0.0266    |
| lightFM CF           | 0.8351  | 0.1083       | 0.0775    |
| lightFM hybrid       | 0.8417  | 0.0560       | 0.0509    |
| lightFM hybrid tuned |      0.8474   |       0.0609       |     0.0639      |
|                      |         |              |           |

## Example

Films watched by user:

| item id |                                                 movie_title | genre                                   |
|--------:|------------------------------------------------------------:|-----------------------------------------|
|     181 |                                   Return of the Jedi (1983) | Action, Adventure, Romance, Sci-Fi, War |
|     260 |                                        Event Horizon (1997) |       Action, Mystery, Sci-Fi, Thriller |
|     320 | Paradise Lost: The Child Murders at Robin Hood Hills (1996) |                             Documentary |
|     321 |                                               Mother (1996) |                                  Comedy |
|     327 |                                             Cop Land (1997) |                   Crime, Drama, Mystery |
|     331 |                                            Edge, The (1997) |                     Adventure, Thriller |
|     340 |                                        Boogie Nights (1997) |                                   Drama |
|     342 |                         Man Who Knew Too Little, The (1997) |                         Comedy, Mystery |
|     346 |                                         Jackie Brown (1997) |                            Crime, Drama |
|     347 |                                          Wag the Dog (1997) |                           Comedy, Drama |

Recommended films:

|  item id|                 movie_title     |                  genre |
|------------:|---------------------------:|--------------------------|
|          12 | Usual Suspects, The (1995) |          Crime, Thriller |
|         195 |     Terminator, The (1984) | Action, Sci-Fi, Thriller |
|         204 |  Back to the Future (1985) |           Comedy, Sci-Fi |
|         234 |                Jaws (1975) |           Action, Horror |
|         258 |             Contact (1997) |            Drama, Sci-Fi |
