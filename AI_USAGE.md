# AI Usage Disclosure

## What I used AI for

I used Claude throughout this project for the following specific purposes:

- Brainstorming the project direction and scope during the initial planning phase
- Generating the initial notebook structure and boilerplate code for the LSTM and Transformer architectures
- Debugging specific issues, including the sliding window function and the backtesting logic
- Explaining concepts I was unfamiliar with, such as how self-attention computes relevance scores between time steps
- Helping structure the markdown descriptions and reflection sections

## What I did not use AI for

- Understanding the LSTM gate mechanism — I worked through how the forget, input, and output gates function independently and can explain each one in my own words
- Selecting the four assets and their industries — the decision to use TSLA, JPM, XOM, and SPY to represent diverse market sectors was my own, based on wanting to test the model across different return dynamics
- Choosing which technical indicators to include — I decided to use daily return, MA5, MA20, and RSI based on my own understanding of what signals are meaningful in financial time series
- Diagnosing why the Transformer underperformed — I identified the prediction collapse by inspecting the raw prediction distributions myself, and reasoned through why a vanilla Transformer might struggle with noisy financial data compared to LSTM

## How I verified AI output

- I ran every generated code cell and verified the output shapes and values made sense
- I caught and fixed several issues myself, such as the split percentage mismatch
- I asked follow-up questions whenever I did not understand why the code was written a certain way before using it

## What I learned from the interaction

Using Claude as a thought partner helped me understand concepts more deeply than just reading documentation. For example, asking "why do we take out[:, -1, :]" forced me to understand that the last timestep summarizes the entire sequence. I also learned that AI explanations need to be verified, several times the generated comments had small inaccuracies that I caught by checking against the actual code.