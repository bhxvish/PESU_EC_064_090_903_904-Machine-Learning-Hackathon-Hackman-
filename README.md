# Hackman: Intelligent Hangman Assistant  
*UE23CS352A: Machine Learning Hackathon Project*
PESU_EC_064_090_903_904
---

## Project Overview

**Hackman** is an intelligent agent designed to play and win the classic game **Hangman** using **Machine Learning**.  
Unlike humans who rely on intuition or letter frequency (like guessing ‘E’ or ‘A’ first), Hackman uses a combination of **probabilistic reasoning** and **reinforcement learning** to make smarter guesses with fewer mistakes.

The agent learns from a large English corpus of 50,000 words and improves its performance through experience.

---

## Problem Statement

> “Design and build an intelligent Hangman assistant that effectively guesses letters to solve puzzles with maximum efficiency.”

Your goal is to:
- Train a **Hidden Markov Model (HMM)** on a given word corpus to estimate the probability of letters appearing in blank positions.
- Use a **Reinforcement Learning (RL)** agent that interacts with a Hangman environment to choose the optimal next letter.
- Maximize the success rate while minimizing wrong and repeated guesses.

---

## System Architecture

The system consists of two core components:

### **1. Hidden Markov Model (HMM)**
- **Purpose:** Acts as the “intuition” of the agent.  
- **Input:** Current game state (masked word, guessed letters).  
- **Output:** Probability distribution over the alphabet (likelihood of each letter appearing).  
- **Design:** Trained using the provided 50,000-word corpus. The model can be length-specific or use special padding tokens.

---

### **2. Reinforcement Learning (RL) Agent**
- **Purpose:** Acts as the “brain” of the system.  
- **Environment:** Custom-built Hangman game simulator.  
- **Agent Design:**
  - **State:** Combination of the masked word, guessed letters, remaining lives, and HMM probabilities.
  - **Actions:** Guessing any unguessed letter (A–Z).
  - **Reward:**  
    - +10 for a correct guess  
    - -5 for a wrong guess  
    - -2 for repeated guesses  
    - +50 for winning a game  
    - -50 for losing a game  
- **Algorithm:** Q-learning / Deep Q-Network (DQN) with ε-greedy exploration.

---

## Dataset

- **File:** `corpus.txt` (50,000 English words)  
- **Usage:** The only valid data source for both training and evaluation.  
- **Rule:** No external word lists or pre-trained language models allowed.

---

## Scoring Formula

The final performance is evaluated as:

```
Final Score = (Success Rate * 2000)
             - (Total Wrong Guesses * 5)
             - (Total Repeated Guesses * 2)
```

---

## Tech Stack

| Category | Tools / Libraries |
|-----------|------------------|
| Language | Python 3.x |
| ML Model | hmmlearn, numpy, pandas, scikit-learn |
| RL Agent | gym, torch / tensorflow (if using DQN) |
| Visualization | matplotlib, seaborn |
| Environment | Custom Hangman game environment |

---

## How to Run

1. **Clone the repository**
   ```bash
   git clone https://github.com/<your-username>/Hackman-ML-Agent.git
   cd Hackman-ML-Agent
   ```

2. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

3. **Run the notebook**
   ```bash
   jupyter notebook ML_DemoO.ipynb
   ```

4. **Train and Evaluate**
   - Train the **HMM** on the corpus.
   - Run the **RL agent** in the Hangman environment.
   - View metrics and plots (reward curves, success rate, etc.).

---


## Key Insights

- **HMMs** capture letter transition patterns effectively for word structure modeling.  
- **RL exploration** (ε-greedy) is crucial for learning optimal guessing strategies.  
- Balancing the reward system helps reduce overfitting to frequent letters.

---

## Future Improvements

- Use a **neural HMM** for deeper language understanding.  
- Add **transfer learning** from pretrained word embeddings (e.g., GloVe, Word2Vec).  
- Implement a **Dueling DQN** or **Policy Gradient** agent for better exploration.  
- Introduce **difficulty levels** (easy → rare words).

---

## Repository Structure

```
Hackman-ML-Agent/
│
├── ML_DemoO.ipynb             # Main notebook
├── corpus.txt                 # Word corpus (training data)
├── Problem_Statement.pdf      # Original problem statement
├── Analysis_Report.pdf         # Detailed project report
├── requirements.txt           # Python dependencies
└── README.md                  # Project documentation
```

---

## Team & Contributors

**Course:** UE23CS352A – Machine Learning Hackathon  
**Department:** Computer Science and Engineering (AIML)
**Team:** S BHAVISH (PES2UG23AM903)
          Saiprasanna (PES2UG23AM090)
          N Yashaswini (PES2UG23AM064)
          Madhulatha (PES2UG23AM904)

---

## License

This project is developed as part of the **UE23CS352A Machine Learning Hackathon** and is intended for educational use only.

---

*If you like this project, don’t forget to star the repo!*
