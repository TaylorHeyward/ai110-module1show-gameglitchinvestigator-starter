# 💭 Reflection: Game Glitch Investigator

Answer each question in 3 to 5 sentences. Be specific and honest about what actually happened while you worked. This is about your process, not trying to sound perfect.

## 1. What was broken when you started?

- What did the game look like the first time you ran it?
- List at least two concrete bugs you noticed at the start  
  (for example: "the hints were backwards").

## 1. What was broken when you started?

- What did the game look like the first time you ran it?
- List at least two concrete bugs you noticed at the start  
  (for example: "the hints were backwards").

When I first ran the game, it technically worked, but the behavior was inconsistent and confusing. The feedback and game flow did not match what the player would expect from a guessing game.
Some of the main bugs I noticed were:
The hint logic was incorrect. For example, when I guessed 1 and the secret number was 55, the game told me to guess lower instead of higher.
The attempts system was inaccurate. The game showed that I had more attempts remaining than I actually did and sometimes revealed the answer before I had used all of my attempts.
The game reset and overall user experience were poor. It was slow to restart, and starting a new game did not feel clean or immediate.

## 2. How did you use AI as a teammate?

- Which AI tools did you use on this project (for example: ChatGPT, Gemini, Copilot)?
- Give one example of an AI suggestion that was correct (including what the AI suggested and how you verified the result).
- Give one example of an AI suggestion that was incorrect or misleading (including what the AI suggested and how you verified the result).

I used AI as a teammate in two main ways: to help refactor game logic into a helper file and to help identify where the bugs were actually coming from.
One correct suggestion the AI gave me was to move the check_guess() function out of app.py and into logic_utils.py using Copilot Agent Mode. It also correctly identified that the high/low feedback logic was reversed. For example, if a guess was higher than the secret, the original code told the player to go higher instead of lower. I verified this by reading the conditional logic in the code and by testing the live game after the refactor. After the change, guesses above the secret returned "Too High" with a lower hint, and guesses below the secret returned "Too Low" with a higher hint.
One incorrect or misleading suggestion I received was assuming that logic_utils.py already contained the real game logic. At first, the file only had placeholder functions with NotImplementedError, so debugging there would not have fixed the actual bugs. I verified that this suggestion was misleading by opening both files and seeing that the working logic still lived in app.py. I then shifted the debugging focus back to app.py until the functions were properly refactored.

---

## 3. Debugging and testing your fixes

- How did you decide whether a bug was really fixed?
- Describe at least one test you ran (manual or using pytest)  
  and what it showed you about your code.
- Did AI help you design or understand any tests? How?


I verified my repairs in two ways. First, I used pytest to test the repaired check_guess() logic in tests/test_game_logic.py. I created tests for a winning guess, a guess that was too high, and a guess that was too low. When I first ran pytest, the test file failed because of an indentation and file-content issue, so I corrected the test file and reran the tests until they passed.
Second, I launched the game locally with Streamlit and tested the repaired behavior in the live app. I checked that guesses above the secret gave a lower hint, guesses below the secret gave a higher hint, and that the game still ran correctly after the refactor. I also reviewed the diffs after using Copilot Agent Mode to make sure the changes in app.py and logic_utils.py were clean and matched the intended repairs.

---

## 4. What did you learn about Streamlit and state?

- How would you explain Streamlit "reruns" and session state to a friend who has never used Streamlit?

Streamlit reruns the entire script every time the user interacts with the app, such as clicking a button or entering input. Instead of updating just one part of the app, it starts from the top again, which can reset variables if they are not stored properly.
Session state acts like memory that persists across reruns. It allows the app to remember values like the secret number, attempts, and score so the game does not restart every time the user makes a guess. I would explain it as: Streamlit constantly refreshes, but session state is what keeps your data from disappearing.

---

## 5. Looking ahead: your developer habits

- What is one habit or strategy from this project that you want to reuse in future labs or projects?
  - This could be a testing habit, a prompting strategy, or a way you used Git.
- What is one thing you would do differently next time you work with AI on a coding task?
- In one or two sentences, describe how this project changed the way you think about AI generated code.

Streamlit reruns the entire script every time the user interacts with the app, such as clicking a button or entering input. Instead of updating just one part of the app, it starts from the top again, which can reset variables if they are not stored properly.
Session state acts like memory that persists across reruns. It allows the app to remember values like the secret number, attempts, and score so the game does not restart every time the user makes a guess. I would explain it as: Streamlit constantly refreshes, but session state is what keeps your data from disappearing.