# Snake Game AI using Deep Q-Network (DQN)

This project implements a Snake game AI using a Deep Q-Network (DQN) approach, a type of reinforcement learning algorithm. The AI learns to play the Snake game by maximizing its score over time through trial and error. Deep Q-Networks (DQN) to train an AI agent to play the Snake game. The AI controls the snake, making decisions in real-time to maximize its score while avoiding collisions. The agent learns to improve its performance by playing multiple games and adjusting its strategy based on rewards and penalties.

## Installation

To run this project locally, you'll need Python and a few dependencies installed. Follow these steps:

1. **Clone the Repository:**
   ```sh
   git clone https://github.com/ShivamGupta92/Reinforcement_learning_SnakeGameA.git
   cd snake-game-ai-dqn
   ```

2. **Create a Virtual Environment:**
   ```sh
   python3 -m venv venv
   source venv/bin/activate   # On Windows: venv\Scripts\activate
   ```

3. **Install Required Packages:**
   ```sh
   pip install -r requirements.txt
   ```

4. **Run the Game:**
   ```sh
   python agent.py
   ```

## Usage

Once the environment is set up, you can start training the AI by running the `agent.py` script. The AI will begin playing the Snake game and gradually learn to improve its score through repeated gameplay.

During the training, the AI's performance (score) will be displayed, and a plot of the scores and the moving average will be shown.

## Reinforcement Learning Approach

The AI uses a **Deep Q-Network (DQN)** for learning how to play the Snake game:

- **Q-Learning:** The AI learns a Q-function, which estimates the expected future rewards for taking a given action in a given state.
- **Deep Neural Network:** The Q-function is approximated using a neural network, allowing the AI to handle the large state space of the game.
- **Rewards:** The AI receives positive rewards for eating food and negative rewards for collisions.

## Model Architecture

The neural network used in this project is a fully connected feedforward network with the following architecture:

- **Input Layer:** Takes in the game state, represented as an 11-dimensional vector.
- **Hidden Layers:**
  - Two hidden layers with ReLU activation.
  - Dropout is applied to the first hidden layer to prevent overfitting.
- **Output Layer:** Outputs Q-values for each possible action (left, right, straight).

### Model Summary

- **Input Size:** 11
- **Hidden Layers:** 256, 512 units
- **Output Size:** 3 (corresponding to the three possible actions)
- **Activation Function:** ReLU
- **Dropout:** 20% applied after the first hidden layer

## Training Process

The training process is handled by the `QTrainer` class, which manages:

- **Forward Pass:** Computes the predicted Q-values for the current state.
- **Loss Calculation:** The loss is calculated as the difference between predicted and target Q-values using SmoothL1Loss.
- **Backpropagation:** The loss is backpropagated to update the model's parameters using the AdamW optimizer.
- **Learning Rate Scheduling:** The learning rate is adjusted periodically to improve convergence.

### Training Details

- **Memory Replay:** The agent stores its experiences in a memory buffer and samples random batches for training to break the correlation between consecutive experiences.
- **Exploration vs. Exploitation:** An epsilon-greedy strategy is used to balance exploration of new strategies and exploitation of known good strategies.
- **Model Saving:** The model is periodically saved to a file (`model.pth`) when it achieves a new high score.

## Customization

You can customize various aspects of the AI and game:

- **Game Settings:** Modify the snake's speed, block size, and screen dimensions in `game.py`.
- **Model Architecture:** Adjust the neural network structure in `model.py`.
- **Training Parameters:** Change learning rate, gamma (discount factor), and memory size in `agent.py`.

## Contributing
   ```sh
- SHIVAM GUPTA
   ```
Contributions are welcome! If you'd like to contribute to this project, please fork the repository and submit a pull request with your improvements.

## License

This project is licensed under the MIT License. See the [MIT LICENSE](LICENSE) file for details.

---
