# 💭 Reflection: Game Glitch Investigator

Answer each question in 3 to 5 sentences. Be specific and honest about what actually happened while you worked. This is about your process, not trying to sound perfect.

## 1. What was broken when you started?

- What did the game look like the first time you ran it? 
- List at least two concrete bugs you noticed at the start  
  
  It looked like an attempt to make a guessing game but with a lot of bugs. One bug I realized was that the hints did not matches the guesses, It would say go higher when it should say go lower and vice versa. Another bug is that the difficulty range for medium and hard is swapped. Also the difficulty setting is not correct because it always resets the secret number from 1 to 100.
---

## 2. How did you use AI as a teammate?

- Which AI tools did you use on this project (for example: ChatGPT, Gemini, Copilot)?
- Give one example of an AI suggestion that was correct (including what the AI suggested and how you verified the result).
- Give one example of an AI suggestion that was incorrect or misleading (including what the AI suggested and how you verified the result).

  I used GitHub Copilot Chat and Copilot Agent mode while working on this project. I used regular Copilot chat for when I have specific problems, and I used Agent mode when I wanted to move the functions from app.py into logic_utils.py. Making each bug in a separate chat helped me stay focused and made it easier to tell whether the AI was actually answering the right problem.
  One AI suggestion that was right was to fix the check_guess function so that it would give the correct messages. That suggestion was correct because after I used it, I tested using streamlit and also copilot also added a pytest case that checked check_guess(60, 50) returns "Too High" and check_guess(40, 50) returns "Too Low". So both the game behavior and the tests matched the expected result.
  One incorrect or misleading AI suggestion happened when Copilot suggested changing the difficulty ranges but it kept getting the secret number from a range of 1-100 instead of using the range we want. At first the change looked correct because the range on the text to the left updated, but when I started a new game the secret number was sometimes out of range. I tested this by just repetedly clicking on new game and seeing if it would go out of range

---

## 3. Debugging and testing your fixes

- How did you decide whether a bug was really fixed?
- Describe at least one test you ran (manual or using pytest)  
  and what it showed you about your code.
- Did AI help you design or understand any tests? How?

To verify that the code really worked, I tested the code in the Streamlit app to see if guessing the secret number gave you the right response(too high for high and too low for low and congradulating for the same guess). SO, I guessed higher and lower than the secret number to make sure the hints now correctly say "Go LOWER" or "Go HIGHER". I also tested the difficulty setting by switching them between easy, hard and normal then clicking new game to see if it would eventually give me the a secret number outside of the range. Copilot deigned the entire pytest that checks the check guess function. The test verifiyed the basic functionallity by just three tests of too high, too low and a guess that is correct
---

## 4. What did you learn about Streamlit and state?

- In your own words, explain why the secret number kept changing in the original app.
- How would you explain Streamlit "reruns" and session state to a friend who has never used Streamlit?
- What change did you make that finally gave the game a stable secret number?

The secret number kept changing in the original because Streamlit reruns the entire script every time the user interacts with the page. So when the code generated the secret number again when it returned, it sometimes changes the original value. I would explain how it reruns to a friend by saying that every time you click a button or enter input, Streamlit runs the whole Python file from top to bottom. To keep important values from resetting each time. Session state acts like memory for the app, letting some values not change/.

The change that made secret number stable was storing it in st.session_state and only getting it if it did not already exist. This stopped the number from being recreated every time the app runs and made the guessing game more consistent.
---

## 5. Looking ahead: your developer habits

- What is one habit or strategy from this project that you want to reuse in future labs or projects?
  - This could be a testing habit, a prompting strategy, or a way you used Git.
- What is one thing you would do differently next time you work with AI on a coding task?
- In one or two sentences, describe how this project changed the way you think about AI generated code.

One habit I want to reuse in future projects is testing bugs one step at a time instead of trying to fix everything at once. One thing I would do differently next time when working with AI is being more carefull with accepting what it says(sometimes it confidently lies). Some suggestions looked correct at first but when you really look at it they just added more lines of code

This project changed the way I think about AI-generated code because I learned that AI can help speed up debugging, but it cannot replace programmers like I feared. Developers still need to supervise the code AI writes.