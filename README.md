# 🎮 Game Glitch Investigator: The Impossible Guesser

## 🚨 The Situation

You asked an AI to build a simple "Number Guessing Game" using Streamlit.
It wrote the code, ran away, and now the game is unplayable. 

- You can't win.
- The hints lie to you.
- The secret number seems to have commitment issues.

## 🛠️ Setup

1. Install dependencies: `pip install -r requirements.txt`
2. Run the broken app: `python -m streamlit run app.py`

## 🕵️‍♂️ Your Mission

1. **Play the game.** Open the "Developer Debug Info" tab in the app to see the secret number. Try to win.
2. **Find the State Bug.** Why does the secret number change every time you click "Submit"? Ask ChatGPT: *"How do I keep a variable from resetting in Streamlit when I click a button?"*
3. **Fix the Logic.** The hints ("Higher/Lower") are wrong. Fix them.
4. **Refactor & Test.** - Move the logic into `logic_utils.py`.
   - Run `pytest` in your terminal.
   - Keep fixing until all tests pass!

## 📝 Document Your Experience

- [ ] Describe the game's purpose.
- [ ] Detail which bugs you found.
- [ ] Explain what fixes you applied.

## 📸 Demo

- [ ] [Insert a screenshot of your fixed, winning game here]

## 🚀 Stretch Features

- [ ] [If you choose to complete Challenge 4, insert a screenshot of your Enhanced Game UI here]


Phase 1:

The first bug I encountered was in the New Game button/state, as everytime a new game is initiated the satte is set to "game over" as if the game had already been played. It is also hardcoding the actual difficulty value and not reset any variables properly, meaning the game's prior history is carried over thus leading to a "game over" as all guesses have been tried already. 

Second bug is related to the backwards feedback messages. As in, the hints are being displayed opposite to what they actually should be. For example, the hint text tells the user to guess higher when in reality the number is lower than what they guessed, and viceversa. 

Third bug is the difficulty setting is set to a different range via hardcode. Hard should return a range of at least 1 - 100, which has more variety, when in reality it is returning 1 - 50, which is the range for Normal. 

Phase 2

For phase 2 I chose to fix the error with New Game not actually starting a new game. What I decided to do to tackle the issue was to explicitly reset the game's status to "playing" at the end of every match so when the page reloads at the the click of new game, the status checker detects that the sessions status = "playing", allowing the game to proceed. 
