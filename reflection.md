# 💭 Reflection: Game Glitch Investigator

Answer each question in 3 to 5 sentences. Be specific and honest about what actually happened while you worked. This is about your process, not trying to sound perfect.

## 1. What was broken when you started?

- What did the game look like the first time you ran it?
- List at least two concrete bugs you noticed at the start
  (for example: "the hints were backwards").

1. The hint logic was incorrect.
   I expected the game to tell me to guess lower when my guess was higher than the secret number, and to guess higher when my guess was lower than the secret number. Instead, the hints were often wrong. For example, when the secret number was 55, I guessed 80 and then 70, but the game still displayed “Go higher,” which was misleading.

2. The game state did not fully reset after clicking “New Game.”
   I expected a new game to clear the old game-over message, reset the input field, and refresh the debug information. Instead, after clicking “New Game,” the interface still showed “Game over. Start a new game to try again,” the previous input stayed in the text box, and the debug info did not fully reset until I manually refreshed the page.

3. The attempts display seemed inconsistent.
   I expected the number of attempts shown in the main UI to match the attempts shown in the Developer Debug Info. Instead, I saw cases where the top message showed “Attempts left: 1” while the debug panel still showed “Attempts: 7,” which suggests the displayed state and the internal state were out of sync.

4. Pressing Enter did not submit the guess.
   I expected pressing Enter in the input box to behave like submitting a guess, especially since the UI text suggested that behavior. Instead, nothing happened unless I clicked the “Submit Guess” button manually.

---

## 2. How did you use AI as a teammate?

- Which AI tools did you use on this project (for example: ChatGPT, Gemini, Copilot)?
- Give one example of an AI suggestion that was correct (including what the AI suggested and how you verified the result).
- Give one example of an AI suggestion that was incorrect or misleading (including what the AI suggested and how you verified the result).

When I highlighted the check_guess function, Copilot correctly identified that the comparison guess > secret should logically lead to a "Go LOWER" hint rather than "Go HIGHER".

## I manually swapped the return strings in the code and then ran the game, confirming that guessing 70 when the secret was 55 now correctly prompts "Go LOWER".

## 3. Debugging and testing your fixes

- How did you decide whether a bug was really fixed?
- Describe at least one test you ran (manual or using pytest)
  and what it showed you about your code.
- Did AI help you design or understand any tests? How?

I verified my repairs in two ways. First, I reran the Streamlit app and tested multiple guesses manually with the Developer Debug Info panel open so I could compare the visible hint against the actual secret value. This helped me confirm that the hint direction was now consistent with the game state.

## Second, I reviewed the submit flow in `app.py` to confirm that the `secret` value stayed as an integer instead of changing type across attempts. I used both code inspection and repeated gameplay to verify that the game behavior no longer changed unpredictably based on attempt count. After each fix, I reran the app instead of assuming the edit was correct just because the code executed without crashing.

## 4. What did you learn about Streamlit and state?

- How would you explain Streamlit "reruns" and session state to a friend who has never used Streamlit?

---

## 5. Looking ahead: your developer habits

- What is one habit or strategy from this project that you want to reuse in future labs or projects?
  - This could be a testing habit, a prompting strategy, or a way you used Git.
- What is one thing you would do differently next time you work with AI on a coding task?
- In one or two sentences, describe how this project changed the way you think about AI generated code.
