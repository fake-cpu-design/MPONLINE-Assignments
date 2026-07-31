# Lunar Lander Reinforcement Learning Agent Training

## Project Overview
This project develops a Deep Q-Network (DQN) to autonomously land a spacecraft on a landing pad using the Gymnasium `LunarLander-v2` environment. The agent learns continuous control strategies through trial and error to maximize its landing score.

## Environment & Problem Statement
* **Environment:** `LunarLander-v2` (Gymnasium Box2D)
* **State Space:** 8 continuous variables (X/Y coordinates, X/Y linear velocities, angle, angular velocity, and two booleans indicating leg contact with the ground).
* **Action Space:** 4 discrete actions (0: Do nothing, 1: Fire left orientation engine, 2: Fire main engine, 3: Fire right orientation engine).
* **Reward:** * +100 to +140 for moving to the landing pad and zeroing velocity.
  * -100 for crashing.
  * +100 for a safe landing.
  * -0.3 points for every frame the main engine is firing.
* **Termination:** The episode finishes if the lander crashes, comes to rest, or flies off-screen.

## Architecture & Algorithm
* **Algorithm:** Deep Q-Learning (DQN)
* **Q-Network:** A Multi-Layer Perceptron (MLP) with two hidden layers of 64 neurons each, using ReLU activations.
* **Experience Replay:** Uses a memory buffer of 100,000 transitions to sample random batches of size 64 for stabilized training.
* **Target Network:** A secondary network updated every 10 episodes to provide stable Q-value targets during loss calculation.
* **Exploration Strategy:** $\epsilon$-greedy strategy starting at 1.0 and decaying dynamically down to 0.01.

## Prerequisites
* Python 3.8+
* Google Colab (GPU recommended)
* `gymnasium[box2d]`, `torch`, `numpy`, `swig`

## Usage
1. Open a new Google Colab notebook.
2. Verify you have a GPU instance active.
3. Run the code cells sequentially from top to bottom.
4. *Note:* The first cell installs `swig` and the `box2d` extension which are mandatory for rendering and interacting with the Lunar Lander environment.