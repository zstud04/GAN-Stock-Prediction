- Lin et al uses GRU as the generator in the GAN model

## Data:
- 10 years history of stock price
- 36 features:
    - Open (opening price at beginning of trading session)
    - High (highest price in session)
    - Low (lowest price in session)
    - Close (price at end of seesion)
    - Volume (total number of shares traded)
    - NASDAQ
    - NYSE
    - S&P
    - FTSE100
    - NIKKI225
    - ...more index funds
    - Crude Oil
    - Gold
    - USD index
    - Amazon
    - Google
    - MSFT
    - MA7 (average price of stock/security over past 7 periods)
    - MACD (trend indicator for bearish/bullish momentum)
    - 20SD (volatility of stock over 20 days)
    - upper_band (level at which a stock could be considered to be overbought)
    - lower_band (level at which a stock could be considered to be underbought)
    - EMA (type of moving avg that places more weight on recent datapoints)
    - log momentum(rate of change of prices in security)
    - absolute of 3 comps(abs value of comparison between current price and last 3 periods)
    - angle of 3 comps (angle of slope between current price and last 3 periods)
    - absolute of 6 comps (... for past 6)
    - angle of 6 comps
    - absolute of 9 comps
    - angle of 9 comps
    - News

## General process

### Generator
- Generator input will be 3-d data:
    - batch size
    - input step
    - features
- Generator output will be 2-d data
    - batch size
    - output step
## Model specs:
- 3 layers of GRU
- 1024, 512, 256 neuron layers
- two layers of dense

### Discriminator
- CNN aimed at distinguishing real/fake input
- input data will be either from original data or the Generator
- 3 1d convoluation layers: 32, 64, 128 neurons
    - +3 dense layers
        -220,220, 1 neuron
- Sigmoid function will give a scalar output for 0 or 1, real or fake
- generated stock price combined with actual stock price data as input

### Hyperparam tuning
in ML every model has a certain # of params that need to be defined in training, plus the number of layers, learning rate, number of neurons.
- Lin et al uses Bayesian optimization for hyperparam optimization
    - finds params that can produce min or max score given objective function


