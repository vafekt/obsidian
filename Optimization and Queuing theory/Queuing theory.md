1. Basic ideas of queuing theory models (parts of queuing systems and their parameters, Kendall classification, stochastic processes, B&D processes and their classification). [10] p. 2 – 6.

- Parts of queuing system:
![[Pasted image 20231221094002.png]]
	- Population of customers: It can be limited or unlimited. 
		- Unlimited population is used in a theoretical system with a large number of possible customers (a bank on a busy street, or petrol station). The number of customers in the system does not affect the arrival process.
		- Limited population can be a number of processes to be run by a computer. The number of customers in the system affects the arrival process.
	- Arrival defines the way customers enter the system. Mostly random with random intervals between two adjacent arrivals. The distribution of arrival is called arrival pattern.
	- Queue represents customers waiting for service (can be empty). Warning: Customers being served are not considered to be in the queue.
		- Maximum queue size: maximum number of customers waiting in the queue.
		- System capacity: the maximum number of customers in the system = maximum queue size + number of service channels
		- Queuing discipline: represent the way the queue is organized
			- FIFO - orderly queue, waiting time minimum
			- LIFO - stack, waiting time maximum
			- SIRO - served in random order
			- Priority queue
	- Service represents some activity taking time and the customers ask. It can a a real service carried on. Typically a service takes random time. Distribution of service duration is called Service pattern.
	- Output represents the way customers leave the system. It is usually ignored by theoretical models but sometimes the customers leaving the system enter the queue again (round robin)
- Definition of Queuing theory: is mathematical models of queuing systems that take input parameters and provide quantitative effectiveness parameters. These parameters describe the system performance.
- Kendall classification
	- Describes the queuing system with 5 symbols: A/B/X/Y/Z
		- A is the arrival pattern (distribution of intervals between successive arrivals). 
		- B is the service pattern (distribution of service duration). 
		- X is the number of parallel service channels. 
		- Y is the restriction on system capacity. Omitted for unlimited queues. 
		- Z is the queue discipline (FIFO, LIFO). Omitted for FIFO or if not specified.
	- These types of distribution can be applied:
		- M is the exponential distribution of intervals between arrivals or service duration respectively (M comes from the adjective Markovian).
![[Pasted image 20231223172159.png]]
			- used **to predict the waiting time until the next event occurs, such as a success, failure, or arrival**. For example, Exponential Distribution can be used to predict: The amount of time it takes a customer to make a purchase in your store (success)
			- A **Poisson distribution** is a discrete [probability distribution](https://www.scribbr.com/statistics/probability-distributions/). It gives the probability of an event happening a certain number of times (_k_) within a given interval of time or space.
			- The Poisson distribution has only one [parameter](https://www.scribbr.com/statistics/parameter-vs-statistic/), λ (lambda), which is the [mean](https://www.scribbr.com/statistics/central-tendency/#mean) number of events. The graph below shows examples of Poisson distributions with different values of λ.
		- Ek is the Erlang type k distribution of intervals or service duration. 
		- D is the symbol for deterministic (known) arrivals and constant service duration. 
		- G is a general (any) distribution. 
		- GI is a general (any) distribution with independent random values
- Stochastic process
	- Is also known as random process (opposite to deterministic process)
	- For each value of t (usually assumed to be time) there is a random variable X(t) - output with values in a certain state space S.
		- If the state space is discrete, the process is called a discrete-state stochastic process
		- If the state space is continuous, the process is called a continuous-state stochastic process
- Birth and Death process
	- Is a stochastic process with continuous time and discrete state space S={0,1,2, ... }
	- from any state n belonging to S\{0} only transitions to the neighboring states n+1 and n-1 are allowed. From state 0, the only allowed transition is to state 1.
	- Classification:
		- Markovian birth-death process has transition probabilities dependent only on the current state (not on the past history how the current state has been reached).
		- Linear Markovian processes have the above probabilities dependent linearly on n and delta t
		- Pure birth process has mi n= 0. Pure death process has delta n = 0.
		- A birth–death process can only transition between adjacent states, meaning the state variable can only increase by one (birth) or decrease by one (death)
	![[Pasted image 20231223193453.png]]

2. Poisson process I (probabilities pn(t) and outline of their derivation, random variables associated with Poisson process and their distribution, use of the Poisson process in practice). [10] p. 6 – 10

3. Poisson process II (forgetfulness property, merging and splitting of Poisson processes, arrival, departure and time average probabilities - PASTA property). [10] p. 10 – 14, 21 – 22.
4. 
5. 
