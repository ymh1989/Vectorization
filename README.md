##Computational cost in Monte Carlo simulation using vectorization##

###Introduction###

This repo contains an implementation of pricing financial derivatives using Monte Calo simulation with vectorization calculation. Generally speaking, computer program spend most of the time in loop process. Especially, Monte Carlo simulation(MCS) in finance is mainly composed of `for-loop` or `while-loop`.

The main purpose of this repo is to introduce the method for increasing performance of MCS using vectorization calculation. The program is performed by Python.

###Methods###

As I mentioned in `Introduction`, `loop` is the main reason for increasing cpu time. It means that the more the number of `loop` and `nested-loop`, the more programs spend more time. In most programs with numerical methods, one of role of `loop` is to handle vector or matrix type data. To improve the performance of vector and matrix operation, several libraries has been developed such as [Eigen-C++](http://eigen.tuxfamily.org/index.php?title=Main_Page), [Boost-C++](http://www.boost.org/), and [Numpy-Python](www.numpy.org/).


###Environment###

- CPU : Intel(R) Core(TM) i5-6400 @ 2.7GHZ
- RAM : DDR3L 16GB PC3-12800
- [Python 2.7](https://www.python.org/), [numpy 1.10.4](http://www.numpy.org/)

###Parameters###

- Test case : European vanilla call option

     | Stock | Strike | Maturity | Riskless <p>interest rate</p>  | Volatility | Number of <p>simulations</p> 
---------- | ----------- | ----------- | ----------- | ----------- | -----------
Parameters | 100.0 | 100.0 | 1.0 | 0.03 | 0.3 | 10<sup>5</sup>, 10<sup>6</sup>, 10<sup>7</sup>

###Result###
- In this repo, I compare the cpu time(seconds) of three version for MCS using [Numpy-Python](www.numpy.org/). The parameters can be modified freely.
- `version 0` : Call random number function every time
- `version 1` : Call random number function at a time such as `(# of simulations × # of time steps)`
- `version 2` : Vectorized path generation and call random number function at a time such as `(# of simulations × # of time steps)`

cpu time(sec) | 10<sup>5</sup>simuls  | 10<sup>6</sup>simuls  | 10<sup>7</sup>simuls
------------ | ------------- | ------------- | -------------
version 0 | 0.1041 | 1.0476 | 10.4986
version 1 | 0.1265 | 1.2581 | 12.5500
version 2 | 0.0061 | 0.0735 | 0.7394
** Exact value of European call option: 13.28331

###Note###
- If you're interested in my works, please visit my [homepage](https://sites.google.com/site/yoomh1989/).