const prompts = {
  1: {
    title: "Pause and Reflect",
    text: "What is one thing you learned today that you want to remember for the future?"
  },
  2: {
    title: "Growth Moment",
    text: "What challenge did you face today, and how did you work through it?"
  },
  3: {
    title: "Connection Check",
    text: "How did you contribute to a class discussion, group activity, or lesson today?"
  },
  4: {
    title: "Question Time",
    text: "What is one question you still have about today's topic, and how could you find the answer?"
  },
  5: {
    title: "Strength Spotlight",
    text: "What skill or strength did you use successfully today, and why was it helpful?"
  },
  6: {
    title: "Next Step",
    text: "What is one goal you want to work on next time, and how will you try to improve?"
  }
};

const dice = document.getElementById("dice");
const rollButton = document.getElementById("rollButton");
const promptTitle = document.getElementById("promptTitle");
const promptText = document.getElementById("promptText");

const diceSymbols = ["⚀", "⚁", "⚂", "⚃", "⚄", "⚅"];

function rollDice() {
  rollButton.disabled = true;
  dice.classList.add("rolling");
  dice.textContent = "?";
  promptTitle.textContent = "Rolling...";
  promptText.textContent = "Thinking of a reflection question for you.";

  const randomNumber = Math.floor(Math.random() * 6) + 1;

  setTimeout(() => {
    dice.classList.remove("rolling");
    dice.textContent = diceSymbols[randomNumber - 1];

    const selectedPrompt = prompts[randomNumber];
    promptTitle.textContent = selectedPrompt.title;
    promptText.textContent = selectedPrompt.text;

    rollButton.disabled = false;
  }, 700);
}

rollButton.addEventListener("click", rollDice);
