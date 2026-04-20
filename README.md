# Aubie Kart: Reinforcement Learning Navigation
## Overview

This project explores how reinforcement learning (RL) can be used to train an autonomous agent to navigate a 3D kart obstacle course in Unity. The agent learns to steer and accelerate while avoiding walls and reaching a target efficiently.

The system is built using Unity ML-Agents and trained with the Proximal Policy Optimization (PPO) algorithm.

## Project Goals
- Train an RL agent to complete a kart obstacle course
- Minimize collisions and inefficient movement
- Evaluate how reward design impacts learning
- Analyze training performance and stability

## Technologies Used
- Unity 3D Engine
- Unity ML-Agents Toolkit
- C# (agent behavior)
- Python (training configuration)
- ONNX (model export)

## How It Works
### Agent Behavior

The agent observes:
- Velocity (x and z directions)
- Angular velocity
- Relative position to the target
- Distance to the target

It outputs:
- Steering value [-1, 1]
- Acceleration value [-1, 1]

From the code:
- Observations are normalized for stability
- Actions are continuous for smooth driving behavior
### Reward System

The reward function is designed to guide learning:
- Positive reward for moving toward the target
- Bonus for reaching the target
- Penalty for hitting walls
- Time penalty to encourage efficiency
- Penalty for not moving (stalling)  
This shaping helps the agent learn navigation strategies over time.

### Training Setup
- Algorithm: PPO (Proximal Policy Optimization)
- Batch size: 1024
- Buffer size: 20480
- Learning rate: 0.0003
- Discount factor (gamma): 0.99

The neural network consists of:
- 2 hidden layers
- 256 units per layer

Training was run over millions of steps using Unity ML-Agents.

## Results
Success rate: 24.38%  
234 successes / 960 episodes

Performance improved over time:
- Early training reward ≈ -60
- Final reward ≈ -15

This shows the agent learned basic navigation and obstacle avoidance.

## Key Files
KartAgent.cs – Main RL agent logic (observations, actions, rewards)  
Training logs – Show reward progression and learning trends  
Final model (.onnx) – Trained neural network
## Limitations
Performance is inconsistent across episodes  
Agent trained on only one environment (limited generalization)  
Physics-based environment introduces variability
## Future Improvements
- Train on multiple tracks for better generalization
- Tune reward function further
- Experiment with different RL algorithms
- Improve success rate and stability
