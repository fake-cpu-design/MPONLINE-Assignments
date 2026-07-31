# Cart-Pole Reinforcement Learning Agent Training

## Project Overview
This project builds and trains a Deep Q-Network (DQN) Reinforcement Learning agent to balance a pole on a moving cart using the standard Gymnasium `CartPole-v1` environment. The goal is to keep the pole balanced vertically by applying left or right forces to the cart.

## Environment & Problem Statement
* **Environment:** `CartPole-v1` (Gymnasium)
* **State Space:** 4 continuous variables (Cart Position, Cart Velocity, Pole Angle, Pole Angular Velocity).
* **Action Space:** Discrete (0: Push cart to the left, 1: Push cart to the right).
* **Reward:** +1 for every step the pole remains upright.
* **Termination:** Pole angle exceeds $\pm 12^\circ$, cart position exceeds $\pm 2.4$, or episode length reaches 500 steps.

## Architecture & Algorithm
* **Algorithm:** Deep Q-Learning (DQN)
* **Q-Network:** Multi-Layer Perceptron (MLP) with 2 hidden layers (128 units each) and ReLU activations.
* **Target Network:** Separate network updated periodically to stabilize Q-value estimation.
* **Experience Replay:** Replay memory buffer (capacity 10,000) to decorrelate consecutive state observations.
* **Exploration Strategy:** $\epsilon$-greedy strategy starting at $\epsilon = 1.0$ with exponential decay down to $\epsilon_{min} = 0.01$.

## Prerequisites
* Python 3.8+
* Google Colab (CPU or GPU runtime)
* `gymnasium`, `torch`, `numpy`

## Usage
1. Open Google Colab.
2. Execute each code cell sequentially from Task 1 through Task 7.
3. Observe the total reward increasing during training as $\epsilon$ decays and the policy stabilizes.