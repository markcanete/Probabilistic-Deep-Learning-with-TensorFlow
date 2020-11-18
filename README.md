# **Probabilistic Deep Learning with TensorFlow**

<img src='https://github.com/mohd-faizy/07T_Probabilistic-Deep-Learning-with-TensorFlow/blob/main/Tensorflow_Dev_png/head.png'>

> **Documentation**: [tfp_api_docs](https://www.tensorflow.org/probability/api_docs/python/tfp)

## **Why is probabilistic programming important for deep learning?**

- The use of statistics to overcome uncertainty is one of the pillars of a large segment of the machine learning. Probabilistic reasoning has long been considered one of the foundations of inference algorithms and is represented is all major machine learning frameworks and platforms.
- Usually the classifications that you have arise and the predictions that we make, don't fall into a single category, or they fall into a category with some confidence level. Incorporating those probabilities is incredibly important for machine learning projects in the real world. Usually there is no single answer. There's this wide spectrum of answers that fall into some common distribution pattern.
- TensorFlow probability gives you the capability to take probabilistic distributions and integrate them directly with your Keras layers. TensorFlow probability despite not being part of TensorFlow Core, is an incredibly important part of the model building process.

## TensorFlow Probability is a library for probabilistic reasoning and statistical analysis.

```python
import tensorflow as tf
import tensorflow_probability as tfp # tfp is a seprate library itself

# Pretend to load synthetic data set.
features = tfp.distributions.Normal(loc=0., scale=1.).sample(int(100e3))
labels = tfp.distributions.Bernoulli(logits=1.618 * features).sample()

# Specify model.
model = tfp.glm.Bernoulli()

# Fit model given data.
coeffs, linear_response, is_converged, num_iter = tfp.glm.fit(
    model_matrix=features[:, tf.newaxis],
    response=tf.cast(labels, dtype=tf.float32),
    model=model)
# ==> coeffs is approximately [1.618] (We're golden!)
```

**TensorFlow Probability (TFP)** is a Python library built on TensorFlow that makes it easy to combine probabilistic models and deep learning on modern hardware (TPU, GPU). It's for data scientists, statisticians, ML researchers, and practitioners who want to encode domain knowledge to understand data and make predictions. TFP includes:

- A wide selection of probability distributions and bijectors.
- Tools to build deep probabilistic models, including probabilistic layers and a `JointDistribution` abstraction.
- Variational inference and Markov chain Monte Carlo.
- Optimizers such as Nelder-Mead, BFGS, and SGLD

[![Watch the video](https://img.youtube.com/vi/BrwKURU-wpk/maxresdefault.jpg)](https://youtu.be/BrwKURU-wpk)

> The TensorFlow Probability library provides a powerful set of tools, for statistical modeling, and makes it easy to extend our use of TensorFlow to probabilistic deep learning models. The TFP library, is part of the wider TensorFlow ecosystem, which contains a number of libraries and extensions for advanced and specialized use cases.

## Main Distributions

### a) Binomial Distribution:

**What is a Binomial Distribution?**

A binomial distribution can be thought of as simply the probability of a **SUCCESS** or **FAILURE** outcome in an experiment or survey that is repeated multiple times. The binomial is a type of distribution that has two possible outcomes (the prefix “bi” means two, or twice). For example, a coin toss has only two possible outcomes: heads or tails and taking a test could have two possible outcomes: pass or fail.
what is a binomial distribution

> A Binomial Distribution shows either **(S)uccess** or **(F)ailure.**
>
> - The **first variable** in the binomial formula, `n`, stands for the number of times the experiment runs.
> - The **second variable**, `p`, represents the probability of one specific outcome.

#### **Criteria**

**Binomial distributions must also meet the following three criteria:**

1. The number of observations or trials is fixed. In other words, you can only figure out the probability of something happening if you do it a certain number of times. This is common sense—if you toss a coin once, your probability of getting a tails is 50%. If you toss a coin a 20 times, your probability of getting a tails is very, very close to 100%.

2. Each observation or trial is independent. In other words, none of your trials have an effect on the probability of the next trial.

3. The probability of success (tails, heads, fail or pass) is exactly the same from one trial to another.

Once you know that your distribution is binomial, you can apply the binomial distribution formula to calculate the probability.A Binomial Distribution shows either (S)uccess or (F)ailure.

In general, if the random variable `X` follows the binomial distribution with parameters `n ∈ ℕ` and `p ∈ [0, 1]`, we write `X ~ B(n, p)`. The probability of getting exactly `k` successes in `n` independent Bernoulli trials is given by the probability mass function:

<img src="https://wikimedia.org/api/rest_v1/media/math/render/svg/b872c2c7bfaa26b16e8a82beaf72061b48daaf8e">

for `k = 0, 1, 2, ..., n,` where

<img src='https://wikimedia.org/api/rest_v1/media/math/render/svg/d33401621fb832dd2f9783e80a906d562f669008'>

is the binomial coefficient, hence the name of the distribution. The formula can be understood as follows: k successes occur with probability <a href="https://www.codecogs.com/eqnedit.php?latex=p^k" target="_blank"><img src="https://latex.codecogs.com/gif.latex?p^k" title="p^k" /></a> and `n − k` failures occur with probability `(1 − p)^(n − k)`.

### b) Poisson Distribution:

Poisson distribution is a statistical distribution that shows how many times an event is likely to occur within a specified period of time. It is used for independent events which occur at a constant rate within a given interval of time.

> The Poisson distribution is used to describe the distribution of rare events in a large population. For example, at any particular time, there is a certain probability that a particular cell within a large population of cells will acquire a mutation. Mutation acquisition is a rare event.

#### Characteristics of a Poisson Distribution

The probability that an event occurs in a given time, distance, area, or volume is the same. Each event is independent of all other events. For example, the number of people who arrive in the first hour is independent of the number who arrive in any other hour.

The Poisson distribution is popular for modeling the number of times an event occurs in an interval of time or space.

A discrete random variable `X` is said to have a Poisson distribution with parameter `λ > 0` if for `k = 0, 1, 2, ...,` the probability mass function of X is given by
<img src='https://wikimedia.org/api/rest_v1/media/math/render/svg/c22cb4461e100a6db5f815de1f44b1747f160048'>

where

- `e` is Euler's number `(e = 2.71828...)`
- `k` is the number of occurrences
- `k!` is the factorial of `k.`

The positive real number `λ` is equal to the expected value of `X` and also to its variance.

<img src='https://wikimedia.org/api/rest_v1/media/math/render/svg/2debd3f9adf97c8af4919aa69ed4a7121b47a737'>

The Poisson distribution can be applied to systems with a large number of possible events, each of which is rare. The number of such events that occur during a fixed time interval is, under the right circumstances, a random number with a Poisson distribution.

### c) Uniform Distribution:

The distribution in which all outcomes are equally likely. for example: A coin also has a uniform distribution because the probability of getting either heads or tails in a coin toss is the same.

#### The probability density function (PDF) of the continuous uniform distribution is:

<img src='https://wikimedia.org/api/rest_v1/media/math/render/svg/b701524dbfea89ed90316dbc48c5b62954d7411c'>

#### The cumulative distribution function (CDF) is:

<img src='https://wikimedia.org/api/rest_v1/media/math/render/svg/e5c664c7665277eea8f74575f4650fa933f28dcb'>

#### Other Resources

- YouTube [StatQuest](https://www.youtube.com/channel/UCtYLUTtgS3k1Fg4y5tAhLbw)

---

# :zero::one: **The TensorFlow Probability library**

---

## :black_circle: **a) Univariate distributions**

**Distribution objects** are vital building blocks to build probabilistic deep learning models as these objects capture the essential operations on probability distributions that we're going to need as we build these models.

## :black_circle: **b) Multivariate distributions**

## :black_circle: **c) The Independent distribution**

## :black_circle: **d) Sampling and log probs**

## :black_circle: **e) Trainable distributions**

---

# :zero::two: **Probabilistic layers and Bayesian neural networks**

---

### Connect with me:

[<img align="left" alt="codeSTACKr | Twitter" width="22px" src="https://cdn.jsdelivr.net/npm/simple-icons@v3/icons/twitter.svg" />][twitter]
[<img align="left" alt="codeSTACKr | LinkedIn" width="22px" src="https://cdn.jsdelivr.net/npm/simple-icons@v3/icons/linkedin.svg" />][linkedin]
[<img align="left" alt="codeSTACKr.com" width="22px" src="https://raw.githubusercontent.com/iconic/open-iconic/master/svg/globe.svg" />][stackexchange ai]

[twitter]: https://twitter.com/F4izy
[linkedin]: https://www.linkedin.com/in/faizy-mohd-836573122/
[stackexchange ai]: https://ai.stackexchange.com/users/36737/cypher

---

![Faizy's github stats](https://github-readme-stats.vercel.app/api?username=mohd-faizy&show_icons=true)

[![Top Langs](https://github-readme-stats.vercel.app/api/top-langs/?username=mohd-faizy&layout=compact)](https://github.com/mohd-faizy/github-readme-stats)
