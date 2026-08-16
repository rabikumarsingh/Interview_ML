# Interview_ML


1. Mean vs. Median
	What it is: The mean is the arithmetic average. The median is the middle value when data is sorted.
	Intuition: The mean is the "center of gravity" of the data; the median is the "50th percentile."
2. Variance & 3. Standard Deviation
	What it is: Variance measures the average squared deviation from the mean. Standard Deviation (SD) is the square root of the variance.
	Intuition: Variance tells you how spread out the data is, but because it's squared, the units are weird (e.g., "dollars squared"). SD brings the metric back to the original units of the data (e.g., "dollars").
	Interview Trap: Why divide by n-1instead of nfor sample variance? This is called Bessel’s correction. We divide by n-1to make the sample variance an unbiased estimator of the population variance. (Because a sample tends to have less spread than the whole population, dividing by nwould underestimate the true variance).
4. Probability Distributions
	What it is: A mathematical function that provides the probabilities of occurrence of different possible outcomes.
	Intuition:
	Discrete: Probability Mass Function (PMF). Examples: Binomial (coin flips), Poisson (events over time).
	Continuous: Probability Density Function (PDF). Examples: Normal, Exponential, Uniform. (Note: For continuous variables, the probability of any exact single value is 0; we calculate probability over a range).
5. Normal Distribution
	What it is: The classic symmetric, bell-shaped curve defined entirely by its mean (μ) and standard deviation (σ).
	Intuition: It represents data where most observations cluster around the central peak, and probabilities for values further away taper off equally in both directions.
	Interview Trap: Know the Empirical Rule (68-95-99.7 rule). ~68% of data falls within 1 SD, ~95% within 2 SD, and ~99.7% within 3 SD.
6. Correlation vs. Covariance
	What it is: Covariance indicates the direction of the linear relationship between two variables. Correlation measures both the direction and strength.
	Intuition: Covariance is scale-dependent (if you change units from meters to centimeters, covariance changes wildly). Correlation is just covariance divided by the product of their standard deviations, scaling it to a strict range of -1 to 1.
	Interview Trap: Does correlation imply causation? No. Also, correlation only measures linear relationships. Two variables can have a perfect non-linear relationship (like y=x^2) but a correlation of 0.
7. Central Limit Theorem (CLT)
	What it is: The theorem stating that the distribution of sample means approximates a normal distribution as the sample size gets larger, regardless of the population's actual distribution.
	Intuition: If you take 1,000 samples of 50 people from a highly skewed population, and plot the means of those 1,000 samples, that plot will be a perfect bell curve.
	Interview Trap: Why is CLT so important? It is the foundational reason we can use parametric statistical tests (like t-tests) and calculate confidence intervals in the real world, even when real-world data isn't perfectly normal. (Rule of thumb: n≥30is usually enough for CLT to kick in).
8. Confidence Interval (CI)
	What it is: A range of values, derived from sample statistics, that is likely to contain the value of an unknown population parameter.
	Interview Trap (CRITICAL): What does a 95% Confidence Interval actually mean? DO NOT SAY: "There is a 95% probability that the true mean lies within this specific interval."
	Correct Answer: "If we were to take 100 different samples and compute a 95% CI for each, approximately 95 of those intervals would contain the true population mean, and 5 would not." (Frequentist interpretation).
9. Hypothesis Testing
	What it is: A formal procedure to investigate our ideas about the world using statistics. We set up a Null Hypothesis (H_0, usually "no effect" or "status quo") and an Alternative Hypothesis (H_1, what we want to prove).
10. p-value
	What it is: The probability of obtaining test results at least as extreme as the results actually observed, under the assumption that the null hypothesis is correct.
	Interview Trap: What is a common misconception about the p-value? People think it is the probability that the null hypothesis is true (e.g., "a p-value of 0.03 means there's a 3% chance the null is true"). This is false. It is the probability of the data given the null, not the probability of the null given the data.
11. Type I & Type II Error
	What it is:
	Type I Error (α): False Positive. You reject the Null Hypothesis when it is actually true. (Crying wolf).
	Type II Error (β): False Negative. You fail to reject the Null Hypothesis when it is actually false. (Missing the wolf).
	Interview Trap: How do you reduce both Type I and Type II errors at the same time? You can't just tweak the significance level (α), because lowering Type I error increases Type II error. The only way to reduce both simultaneously is to increase the sample size.
12. Bayes Theorem
	What it is: P(A∣B)=(P(B∣A)⋅P(A))/P(B) . It describes the probability of an event, based on prior knowledge of conditions that might be related to the event.
	Intuition: It’s a mathematical way to update your beliefs. Prior Belief ×New Evidence = Updated Belief (Posterior).
	Interview Trap: Be ready for a "Base Rate Fallacy" question. (e.g., "A disease affects 1 in 1,000 people. A test is 99% accurate. If you test positive, what is the chance you have the disease?" Answer: It's actually only about 9%, because the disease is so rare. Bayes theorem accounts for the low base rate).
12. Bayes Theorem
	What it is: P(A∣B)=(P(B∣A)⋅P(A))/P(B) . It describes the probability of an event, based on prior knowledge of conditions that might be related to the event.
	Intuition: It’s a mathematical way to update your beliefs. Prior Belief ×New Evidence = Updated Belief (Posterior).
	Interview Trap: Be ready for a "Base Rate Fallacy" question. (e.g., "A disease affects 1 in 1,000 people. A test is 99% accurate. If you test positive, what is the chance you have the disease?" Answer: It's actually only about 9%, because the disease is so rare. Bayes theorem accounts for the low base rate).
13. Maximum Likelihood Estimation (MLE)
	What it is: A method of estimating the parameters of a statistical model by finding the parameter values that maximize the likelihood of making the observations given the parameters.
	Intuition: "Given the data I actually see, what model parameters make this data most probable?"
	Interview Trap: How does MLE relate to Ordinary Least Squares (OLS) in linear regression? If you assume the errors in linear regression are normally distributed, maximizing the likelihood (MLE) yields the exact same coefficient estimates as minimizing the sum of squared errors (OLS).
14. Multicollinearity
	What it is: A situation in multiple regression where two or more independent variables are highly correlated.
	Intuition: If X_1and X_2move together perfectly, the model doesn't know which one is actually causing the change in Y.
	Interview Trap: Does multicollinearity affect the predictive power of the model? No, the overall model predictions (R^2) can still be great. What does it affect? It inflates the standard errors of the individual coefficients, making them unstable, unreliable, and hard to interpret. How to fix it? Drop one of the variables, use PCA, or use regularization (Ridge/Lasso).
15. Bias-Variance Tradeoff
	What it is: The property of a model where minimizing Bias increases Variance, and vice versa.
	Bias: Error from erroneous assumptions in the learning algorithm (leads to Underfitting).
	Variance: Error from sensitivity to small fluctuations in the training set (leads to Overfitting).
	Intuition: Total Error = Bias$^2$ + Variance + Irreducible Error. You want a model that is complex enough to capture the true signal (low bias) but not so complex that it memorizes the noise (low variance).
	Interview Trap: How does this apply to specific algorithms?
	Linear Regression: High Bias, Low Variance.
	Decision Trees / KNN (with low K): Low Bias, High Variance.
	How do we fix high variance? Add more data, reduce features, or use Bagging (Random Forest). How do we fix high bias? Add more features, increase model complexity, or use Boosting.



1. Trend & 2. Seasonality
	What they are: Trend is the long-term progression or direction of the series (e.g., global temperatures rising). Seasonality is a repeating, fixed-frequency pattern (e.g., ice cream sales peaking every July).
	Interview Trap: What is the difference between Seasonality and Cyclicality? Cycles (like economic recessions) fluctuate but do not have a fixed frequency. Seasonality always has a fixed, known period (e.g., 12 months, 7 days).
3. Stationarity
	What it is: A time series is stationary if its statistical properties—mean, variance, and autocovariance—are constant over time. It has no trend or seasonality.
	Interview Trap (CRITICAL): Why do we care about stationarity? Because most statistical forecasting models (like ARIMA) assume the data is stationary. If the mean is changing (trend), the model's past learnings won't apply to the future. How do we make data stationary? Differencing (subtracting yesterday's value from today's) or transformations (like Log or Box-Cox to stabilize variance).

4. White Noise vs. 5. Random Walk
	White Noise: A sequence of completely random, independent variables with a mean of zero and constant variance. It has zero autocorrelation. You cannot forecast it.
	Random Walk: A series where the next value is equal to the current value plus a random white noise shock (Y_t=Y_(t-1)+ϵ_t).
	Interview Trap: Is a Random Walk stationary? No. Because its variance grows infinitely over time. Is it white noise? No. White noise has no autocorrelation, but a random walk is highly autocorrelated with its past.

6. Moving Average (MA) & 7. Weighted Moving Average
	What they are: Forecasting the next period by taking the simple average (or weighted average) of the last kperiods.
	Interview Trap (CRITICAL): In classical smoothing, "Moving Average" means averaging past actual values. In ARIMA modeling, the "MA" component means modeling past forecast errors. Do not confuse these two in an interview.
8. Exponential Smoothing (Simple)
	What it is: Instead of giving equal weight to the last kperiods, it applies exponentially decreasing weights to all past observations. It requires one parameter: α(smoothing factor between 0 and 1).
	Intuition: High α(close to 1) means you react quickly to recent changes. Low αmeans you smooth out noise and rely more on history.
9. Holt’s Method (Double Exponential Smoothing)
	What it is: Simple exponential smoothing cannot handle Trend. Holt’s method adds a second equation to capture the trend. It uses two parameters: α(for the level) and β(for the trend).

9. Holt’s Method (Double Exponential Smoothing)
	What it is: Simple exponential smoothing cannot handle Trend. Holt’s method adds a second equation to capture the trend. It uses two parameters: α(for the level) and β(for the trend).
10. Holt-Winters (Triple Exponential Smoothing)
	What it is: Holt’s method cannot handle Seasonality. Holt-Winters adds a third equation for the seasonal component. It uses three parameters: α(level), β(trend), and γ(seasonality).
	Interview Trap: Additive vs. Multiplicative seasonality. Use Additive if the seasonal fluctuations are roughly constant in absolute size. Use Multiplicative if the seasonal fluctuations grow proportionally as the trend increases (very common in retail/sales).

