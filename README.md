# POLICY ITERATION ALGORITHM

## AIM


To develop a Python program to find the optimal policy for the given MDP using the policy iteration algorithm.

## PROBLEM STATEMENT


The aim of this experiment is to find optimal policy for the mdp using policy iteration. Policy iteration includes policy evaluation and policy improvement where evaluation function is used to find optimal value function of each state and then improvement function is used to find best policy by comparing all the action value function as well as policy.


## POLICY ITERATION ALGORITHM

Step1 : We are going to do policy evaluation of each state to get the state value function where the initial policy is defined randomly to the MDP.

Step2: Once we obtain convergence in the policy evaluation then implement policy improvement where we are going to find best optimal policy until the previous and current policy are same.


## POLICY IMPROVEMENT FUNCTION
### Name: M.K.Suriya prakash
### Register Number: 212224110053
```

def policy_improvement(V, P, gamma=1.0):
    Q = np.zeros((len(P), len(P[0])), dtype=np.float64)
    # Write your code here to improve the given policy
    for s in range(len(P)):
      for a in range(len(P[s])):
        for prob,next_state,reward,done in P[s][a]:
          Q[s][a]+=prob*(reward+gamma*V[next_state]*(not done))
          new_pi=lambda s:{s:a for s, a in enumerate(np.argmax(Q,axis=1))}[s]
    return new_pi







```
## POLICY ITERATION FUNCTION
### Name: M.K.Suriya prakash
### Register Number:212224110053
```python

def policy_iteration(P, gamma=1.0, theta=1e-10):
  random_actions=np.random.choice(tuple(P[0].keys()),len(P))
   pi = lambda s: {s:a for s, a in enumerate(random_actions)}[s]
   while True:
    old_pi = {s:pi(s) for s in range(len(P))}
    V = policy_evaluation(pi, P,gamma,theta)
    pi = policy_improvement(V,P,gamma)
    if old_pi == {s:pi(s) for s in range(len(P))}:
      break
   return V, pieration function





```

## OUTPUT:
### 1. Policy, Value function and success rate for the Adversarial Policy
![Screenshot 2025-04-11 142910](https://github.com/user-attachments/assets/a6299a84-dbce-4a4a-9054-88eb28e26d38)

![Screenshot 2025-04-11 142949](https://github.com/user-attachments/assets/9cd3ecd5-187e-4d31-be03-e58ead1bc7ae)
![Screenshot 2025-04-11 143107](https://github.com/user-attachments/assets/0d73469d-17f8-4338-bb41-fb7cea08573c)


### 2. Policy, Value function and success rate for the Improved Policy


![Screenshot 2025-04-11 143125](https://github.com/user-attachments/assets/6308b7a7-166d-4b18-989a-73ce3636a02b)
![Screenshot 2025-04-11 143140](https://github.com/user-attachments/assets/1aef8c3f-a953-4bf0-b4da-c267245c3cd9)
![Screenshot 2025-04-11 143146](https://github.com/user-attachments/assets/4599193e-1d41-4595-b77a-675da02c8758)

</br>

### 3. Policy, Value function and success rate after policy iteration
![Screenshot 2025-04-11 143332](https://github.com/user-attachments/assets/da9c47d8-267c-4d6f-bfe1-ce6ac186ddf3)
![Screenshot 2025-04-11 143343](https://github.com/user-attachments/assets/42094ab6-9238-4e49-936f-fd7a752a67a3)

![Screenshot 2025-04-11 143349](https://github.com/user-attachments/assets/e32d039c-9984-44ae-930e-d088fb178b92)


## RESULT:

Thus, The Python program to find the optimal policy for the given MDP using the policy iteration algorithm is successfully executed.
